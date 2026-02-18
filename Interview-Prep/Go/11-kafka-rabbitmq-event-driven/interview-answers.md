<div dir="rtl" align="right">
پاسخ‌های کامل سوالات Kafka + RabbitMQ + Event-Driven (Go)

بخش پایه

1) تفاوت اصلی Kafka و RabbitMQ چیست؟
پاسخ:
- Kafka log توزیع‌شده و append-only است؛ برای stream و replay عالی است.
- RabbitMQ broker پیام با routing انعطاف‌پذیر exchange/binding است.
- Kafka throughput بالا و retention بلندمدت قوی دارد.
- RabbitMQ برای task queue، الگوهای routing و latency عملیاتی ساده‌تر مناسب است.

2) چرا consumer باید idempotent باشد؟
پاسخ:
- در اکثر سیستم‌ها delivery حداقل یک‌بار است، پس تکرار طبیعی است.
- idempotency جلوی side-effect تکراری (مثلا دوبار ثبت پرداخت) را می‌گیرد.
- با کلید یکتا، dedup table یا state machine قابل پیاده‌سازی است.
- بدون این ویژگی، retry به فساد داده تبدیل می‌شود.

3) DLQ چه زمانی لازم می‌شود؟
پاسخ:
- وقتی پیام پس از retries هنوز fail می‌شود.
- برای جداکردن poison message از مسیر سالم سیستم.
- امکان triage دستی و replay کنترل‌شده می‌دهد.
- شرط لازم: فرآیند عملیاتی روشن برای بررسی DLQ.

بخش متوسط

1) outbox pattern چه مشکلی را حل می‌کند؟
پاسخ:
- ناهماهنگی DB و broker را حذف می‌کند.
- write بیزنسی و event در یک transaction ثبت می‌شوند.
- publisher جداگانه با اطمینان event را ارسال می‌کند.
- در crash بین commit/publish داده از دست نمی‌رود.

2) چگونه ordering را در event processing مدیریت می‌کنی؟
پاسخ:
- ordering را per-key نگه می‌دارم (partition key مثل order_id).
- global ordering را فقط در صورت ضرورت شدید می‌پذیرم چون هزینه بالاست.
- handler را نسبت به out-of-order tolerant طراحی می‌کنم.
- version یا sequence check برای رد پیام قدیمی استفاده می‌شود.

3) retry policy خوب چه اجزایی دارد؟
پاسخ:
- طبقه‌بندی خطا: transient/permanent.
- backoff نمایی + jitter + max attempt.
- timeout و circuit breaker برای dependency خارجی.
- پس از سقف retry، انتقال به DLQ با metadata کامل.

4) چه زمانی RabbitMQ بهتر از Kafka است؟
پاسخ:
- workflow task-oriented با routing پیچیده و ack دقیق.
- وقتی replay طولانی‌مدت لازم نیست.
- وقتی latency و عملیات ساده برای تیم اولویت دارد.
- برای رویداد تحلیلی حجیم و fan-out بالا، Kafka معمولا مناسب‌تر است.

بخش پیشرفته

1) saga orchestration vs choreography را مقایسه کن.
پاسخ:
- orchestration: یک coordinator جریان را کنترل می‌کند؛ قابل‌درک‌تر اما SPOF منطقی ممکن.
- choreography: سرویس‌ها با event مستقل واکنش می‌دهند؛ decouple اما tracing پیچیده‌تر.
- انتخاب به پیچیدگی domain و بلوغ تیم بستگی دارد.
- در هر دو، compensation و idempotency حیاتی است.

2) چگونه event versioning بدون شکستن مصرف‌کننده انجام می‌دهی؟
پاسخ:
- schema registry/contract policy تعریف می‌کنم.
- field جدید optional، field حذف‌شده deprecated و سپس sunset.
- compatibility تست در CI بین producer/consumer.
- rollout تدریجی: consumer tolerant-first سپس producer update.

3) برای high lag در Kafka چه برنامه عملی داری؟
پاسخ:
- اول bottleneck consumer (CPU/I/O/dependency latency) را مشخص می‌کنم.
- scale consumer group و بهینه‌سازی batch size/poll config.
- افزایش partition در صورت نیاز و rebalance مدیریت‌شده.
- backpressure upstream و اولویت‌بندی topicهای بحرانی.

4) سناریوی poison message را end-to-end تحلیل کن.
پاسخ:
- پیام malformed یا ناسازگار با schema باعث fail تکراری می‌شود.
- retry بی‌پایان lag ایجاد می‌کند و جریان سالم را مختل می‌کند.
- با detect threshold به DLQ منتقل می‌شود و alert می‌دهد.
- بعد از fix کد/schema، replay کنترل‌شده انجام و RCA ثبت می‌شود.
</div>
