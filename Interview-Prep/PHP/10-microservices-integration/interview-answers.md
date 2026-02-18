<div dir="rtl" align="right">
پاسخ‌های کامل سوالات Microservices Integration (PHP)

بخش پایه

1) چه زمانی microservice بهتر از monolith است؟
پاسخ:
- وقتی domainها مستقل و تیم‌ها نیاز به release مستقل دارند.
- scale/availability متفاوت بین قابلیت‌ها لازم است.
- complexity عملیاتی قابل تحمل باشد.
- برای تیم کوچک یا domain ساده، monolith معمولا بهتر است.

2) sync و async communication چه تفاوتی دارند؟
پاسخ:
- sync پاسخ فوری و ساده‌تر برای سازگاری لحظه‌ای.
- async decouple و resilientتر برای بار/اختلال.
- sync latency chain می‌سازد، async eventual consistency می‌آورد.
- معماری واقعی ترکیبی از هر دو است.

3) API contract چرا مهم است؟
پاسخ:
- مرز همکاری تیم‌ها را پایدار می‌کند.
- تغییرات ناسازگار زود تشخیص داده می‌شود.
- onboarding و نگهداری آسان‌تر می‌شود.
- بدون contract، integration bug زیاد می‌شود.

بخش متوسط

1) چگونه یک capability را از monolith جدا می‌کنی؟
پاسخ:
- bounded context مناسب انتخاب می‌کنم.
- contract/API واضح و anti-corruption layer می‌گذارم.
- dual-run/strangler migration تدریجی.
- observability و rollback در هر گام.

2) consistency بین سرویس‌ها را چگونه مدیریت می‌کنی؟
پاسخ:
- strong consistency فقط در نقاط بحرانی.
- event-driven + saga برای جریان‌های چندمرحله‌ای.
- idempotency و deduplication در consumer.
- reconciliation job برای ترمیم mismatch.

3) distributed transaction را با چه الگوهایی جایگزین می‌کنی؟
پاسخ:
- saga (orchestration/choreography).
- outbox/inbox و compensation action.
- state machine شفاف برای هر مرحله.
- observability برای تشخیص stuck workflow.

4) چگونه error handling بین سرویس‌ها را استاندارد می‌کنی؟
پاسخ:
- taxonomy خطا (business/transient/system).
- status code و error payload یکپارچه.
- retry policy مبتنی بر نوع خطا.
- correlation id مشترک بین سرویس‌ها.

بخش پیشرفته

1) migration roadmap از Laravel monolith به معماری hybrid (PHP+Go) را توضیح بده.
پاسخ:
- hotspotهای latency/concurrency را انتخاب می‌کنم.
- سرویس Go با contract پایدار و boundary روشن استخراج می‌شود.
- مسیرها تدریجی route می‌شوند و metric impact سنجیده می‌شود.
- پس از پایداری، منطق duplicate حذف می‌شود.

2) چگونه از data duplication ناسالم جلوگیری می‌کنی؟
پاسخ:
- ownership داده روشن (single writer per domain).
- replication هدفمند فقط برای read model.
- version/timestamp و conflict strategy.
- policy retention و reconciliation برای کپی‌ها.

3) یک سناریوی شکست زنجیره‌ای را تحلیل و mitigation کن.
پاسخ:
- dependency پرداخت کند می‌شود -> request queue رشد -> timeout chain.
- mitigation: timeout کوتاه، circuit breaker، fallback deferred payment.
- queue isolation برای مسیرهای بحرانی.
- postmortem برای capacity planning و guardrail بهتر.

4) چگونه ownership سرویس‌ها را در تیم‌های متعدد مدیریت می‌کنی؟
پاسخ:
- owner مشخص، SLO و on-call مسئول هر سرویس.
- interface ownership و change policy روشن.
- runbook و docs اجباری برای handover.
- dashboards مشترک برای دید end-to-end.
</div>
