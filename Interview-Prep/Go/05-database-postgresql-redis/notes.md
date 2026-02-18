<div dir="rtl" align="right">
# Database Notes (PostgreSQL + Redis)

## هدف
تسلط بر SQL design، performance tuning و cache strategy.

## مباحث کلیدی
- ابتدا data model صحیح، سپس optimization.
- index مناسب با الگوی query انتخاب می‌شود؛ هر index هزینه write دارد.
- `EXPLAIN ANALYZE` ابزار اصلی تشخیص bottleneck query.
- transaction isolation level را بر اساس نیاز consistency انتخاب کن.
- Redis برای cache/session/rate-limit/ephemeral data عالی است، نه منبع حقیقت اصلی.
- cache invalidation باید صریح باشد (TTL + event-based invalidation).
- برای race روی موجودی/پرداخت از lock منطقی یا optimistic concurrency استفاده کن.

## نکات مصاحبه‌ای
- N+1 query را تشخیص بده و راه‌حل مشخص ارائه کن.
- بین read replica، caching و query optimization مقایسه trade-off انجام بده.

## تمرین سریع
- یک query کند را با index و rewrite بهبود بده و قبل/بعد را اندازه بگیر.
</div>
