<div dir="rtl" align="right">
# Microservices Integration Notes (PHP)

## هدف
آمادگی برای سوالات یکپارچه‌سازی Laravel با سرویس‌های Go و سیستم‌های توزیع‌شده.

## مباحث کلیدی
- تعریف boundary روشن بین سرویس‌ها از coupling شدید جلوگیری می‌کند.
- ارتباط sync (HTTP/gRPC) برای پاسخ فوری، async (queue/event) برای decouple.
- قرارداد API/event باید versioned و backward-compatible باشد.
- timeout/retry/circuit breaker برای call بیرونی ضروری است.
- idempotency و deduplication در processing async کلیدی‌اند.
- observability بین سرویس‌ها با trace id یکپارچه شود.
- migration تدریجی از monolith به service extraction امن‌تر است.

## نکات مصاحبه‌ای
- روی مرحله‌بندی migration تاکید کن: انتخاب دامنه کوچک، اندازه‌گیری، rollback.
- اول reliability، بعد پیچیدگی تکنیکی اضافه کن.

## تمرین سریع
- یک دامنه از Laravel monolith را به سرویس جدا با event integration تقسیم کن.
</div>
