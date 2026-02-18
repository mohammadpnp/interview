<div dir="rtl" align="right">
# Testing + Quality Notes (PHP/Laravel)

## هدف
افزایش اطمینان از کیفیت و جلوگیری از regression در توسعه سریع.

## مباحث کلیدی
- Unit test برای منطق خالص، Feature test برای endpoint و integration.
- fixture/data setup باید ساده و تکرارپذیر باشد.
- test pyramid: تست‌های سریع بیشتر، E2E کمتر اما هدفمند.
- static analysis (PHPStan/Psalm) خطاهای پنهان را زودتر پیدا می‌کند.
- coding standard با Pint/PHPCS برای یکپارچگی تیمی.
- CI باید lint + test + quality gate داشته باشد.

## نکات مصاحبه‌ای
- روی پایداری تست تمرکز کن، نه صرفا coverage بالا.
- مثال واقعی از bug که با test جلوگیری شده ارائه بده.

## تمرین سریع
- برای یک ماژول حساس، unit + feature + integration تست بنویس.
</div>
