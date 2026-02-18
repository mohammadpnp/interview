<div dir="rtl" align="right">
# Message Queues Notes (Go)

## هدف
پاسخ به سوالات asynchronous processing و event-driven integration.

## مباحث کلیدی
- Queue برای decoupling و smoothing spike بسیار مفید است.
- semantics مهم: at-most-once، at-least-once، exactly-once تقریبی.
- consumer باید idempotent باشد چون duplicate delivery طبیعی است.
- retry باید با backoff و dead-letter queue کنترل شود.
- ordering در همه سیستم‌ها تضمین کامل ندارد؛ design باید تحمل کند.
- monitoring صف: lag، retry rate، DLQ size.
- outbox pattern برای سازگاری DB write و event publish کاربردی است.

## نکات مصاحبه‌ای
- در پاسخ‌ها latency async vs sync trade-off را بیان کن.
- برای رویدادهای مالی/حساس، auditability را در نظر بگیر.

## تمرین سریع
- یک consumer با retry محدود + DLQ + idempotency key پیاده کن.
</div>
