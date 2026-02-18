<div dir="rtl" align="right">
# Microservices + gRPC Notes

## هدف
درک عملی ارتباط سرویس‌ها، قراردادها، خطا، و پایداری در محیط distributed.

## مباحث کلیدی
- gRPC برای ارتباط داخلی low-latency و strongly-typed مناسب است.
- REST برای public API و اکوسیستم متنوع کلاینت‌ها رایج‌تر است.
- schema-first با Protobuf: backward compatibility را جدی بگیر.
- timeout/deadline برای هر درخواست بین‌سرویسی اجباری است.
- retry باید با idempotency key و policy کنترل‌شده باشد.
- circuit breaker و rate limit برای جلوگیری از cascading failure مهم‌اند.
- observability: trace id در کل زنجیره درخواست حمل شود.

## نکات مصاحبه‌ای
- همیشه درباره failure mode صحبت کن (timeout، partial failure، network split).
- API versioning و deprecation plan داشته باش.

## تمرین سریع
- یک service proto تعریف کن و client با deadline + retry بنویس.
</div>
