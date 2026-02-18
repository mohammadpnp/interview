<div dir="rtl" align="right">
# REST API Design Notes (PHP)

## هدف
طراحی API استاندارد، قابل نسخه‌بندی و مناسب برای وب/موبایل.

## مباحث کلیدی
- naming ریسورس‌ها و HTTP method باید معنایی و ثابت باشد.
- status code صحیح بخشی از contract است.
- pagination، filtering، sorting باید استاندارد و مستند باشند.
- API versioning را از ابتدا پیش‌بینی کن.
- idempotency در endpointهای حساس (payment/order) الزامی است.
- error model یکپارچه (`code`, `message`, `details`) طراحی کن.
- rate limiting و authentication/authorization جزو design اولیه‌اند.

## نکات مصاحبه‌ای
- backward compatibility و deprecation plan را حتما توضیح بده.
- API فقط endpoint نیست؛ قرارداد داده و رفتار هم هست.

## تمرین سریع
- یک API قراردادمحور با OpenAPI spec طراحی کن.
</div>
