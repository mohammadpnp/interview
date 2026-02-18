# Kafka + RabbitMQ + Event-Driven Notes (Go)

## هدف
آمادگی برای سوالات Event-Driven Architecture که در آگهی‌های جدید بک‌اند زیاد دیده می‌شود.

## مباحث کلیدی
- Kafka برای stream/event log با throughput بالا و replay مناسب است.
- RabbitMQ برای routing منعطف (exchange/binding) و task queue عملیاتی عالی است.
- at-least-once رایج‌ترین حالت است؛ پس consumer باید idempotent باشد.
- الگوهای مهم: Outbox، Inbox، Saga، Dead Letter Queue.
- ordering را فقط در scope محدود (مثلا partition key) می‌توان حفظ کرد.
- schema evolution برای رویدادها اجباری است (versioning).
- monitoring: consumer lag، retry rate، DLQ size.

## نکات مصاحبه‌ای
- بین Kafka و RabbitMQ تصمیم مطلق نده؛ use-case محور پاسخ بده.
- همیشه failure-mode (duplicate, poison message, reprocessing) را توضیح بده.

## تمرین سریع
- یک جریان OrderCreated -> PaymentProcessed با outbox + idempotent consumer طراحی کن.
