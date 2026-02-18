<div dir="rtl" align="right">
پاسخ‌های کامل سوالات Kafka + RabbitMQ + Event-Driven (PHP)

بخش پایه

1) چرا queue در سیستم‌های پرترافیک مفید است؟
پاسخ:
- spike ترافیک را absorb می‌کند و مسیر synchronous را سبک نگه می‌دارد.
- producer و consumer را decouple می‌کند.
- retry مستقل و resiliency بالاتر می‌دهد.
- trade-off: visibility/consistency complexity.

2) Kafka و RabbitMQ چه تفاوت عملی دارند؟
پاسخ:
- Kafka برای event stream و replay در scale بالا مناسب است.
- RabbitMQ برای task queue و routing انعطاف‌پذیر عالی است.
- Kafka retention محور است؛ RabbitMQ queue lifecycle محور.
- انتخاب باید use-case driven باشد نه صرف محبوبیت ابزار.

3) DLQ چه نقشی دارد؟
پاسخ:
- پیام‌های غیرقابل پردازش را از مسیر اصلی جدا می‌کند.
- از قفل شدن queue اصلی جلوگیری می‌کند.
- امکان triage و replay کنترل‌شده فراهم می‌سازد.
- بدون process عملیاتی، DLQ فقط انبار خطاست.

بخش متوسط

1) چگونه outbox pattern را در Laravel پیاده می‌کنی؟
پاسخ:
- در transaction اصلی، ردیف business و outbox row را همزمان می‌نویسم.
- worker/publisher outbox را poll/publish می‌کند.
- status ارسال و retry ثبت می‌شود.
- idempotency برای جلوگیری از ارسال تکراری لازم است.

2) idempotency را در Jobها چگونه تضمین می‌کنی؟
پاسخ:
- کلید یکتا برای هر عملیات و unique constraint.
- check-before-act یا upsert حالت پردازش.
- side effectها باید در برابر replay امن باشند.
- audit trail برای trace عملیات تکراری.

3) چه زمانی job sync بهتر از async است؟
پاسخ:
- وقتی نتیجه فوری برای UX/business لازم است.
- وقتی failure handling پیچیده async ارزش ندارد.
- وقتی عملیات سبک و deterministic است.
- برای کارهای کند و قابل‌تعویق، async بهتر است.

4) retry مناسب برای خطاهای transient چیست؟
پاسخ:
- backoff نمایی + jitter + max attempt.
- timeout و قطع retry برای خطاهای permanent.
- observability روی retry cause.
- حرکت به DLQ پس از سقف تلاش.

بخش پیشرفته

1) saga pattern را در workflow سفارش/پرداخت توضیح بده.
پاسخ:
- هر سرویس تراکنش محلی خود را انجام می‌دهد و event منتشر می‌کند.
- در failure، compensation action اجرا می‌شود.
- coordinator یا choreography مسیر را مدیریت می‌کند.
- idempotency و timeout handling شرط موفقیت است.

2) اگر duplicate event زیاد شد چه می‌کنی؟
پاسخ:
- dedup key و window زمانی را enforce می‌کنم.
- بررسی misconfig retry/ack broker.
- producer idempotent config در صورت پشتیبانی.
- monitor نرخ duplicate و RCA ریشه‌ای.

3) strategy بازپخش eventهای از دست‌رفته چیست؟
پاسخ:
- checkpoint/offset management دقیق.
- replay از log/outbox با idempotent consumer.
- replay مرحله‌ای برای جلوگیری از overload.
- validation بعد replay برای consistency.

4) اگر backlog بسیار بزرگ شد، چه برنامه عملیاتی داری؟
پاسخ:
- scale consumer و افزایش parallelism کنترل‌شده.
- اولویت‌بندی queueهای حیاتی.
- کاهش work per message (batching/cache).
- throttle producer موقت تا رسیدن به steady state.
</div>
