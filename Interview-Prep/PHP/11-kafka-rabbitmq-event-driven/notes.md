<div dir="rtl" align="right">
# Kafka + RabbitMQ + Event-Driven Notes (PHP/Laravel)

## هدف
تسلط روی event-driven integration در پروژه‌های Laravel و معماری hybrid.

## مباحث کلیدی
- Laravel queue abstraction خوب است، ولی semantics broker را باید بشناسی.
- RabbitMQ برای workflow صف‌محور و routing پیچیده مناسب است.
- Kafka برای event stream تحلیلی/توزیع‌شده با مصرف‌کننده‌های متعدد مناسب است.
- outbox pattern برای همگام‌سازی DB write و publish event مهم است.
- consumer باید idempotent باشد و deduplication داشته باشد.
- retry با backoff و DLQ کنترل شود.
- monitoring queue backlog و failure trend ضروری است.

## نکات مصاحبه‌ای
- بین sync API و async event trade-off را شفاف بیان کن.
- ترتیب پردازش، تکرار پیام، و consistency را در پاسخ پوشش بده.

## تمرین سریع
- یک Job consumer بنویس که idempotency key و DLQ strategy داشته باشد.
</div>
