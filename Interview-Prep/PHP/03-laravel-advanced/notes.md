# Laravel Advanced Notes

## هدف
پوشش قابلیت‌های حرفه‌ای Laravel که در رزومه شما هم آمده‌اند.

## مباحث کلیدی
- Queue/Job برای کارهای زمان‌بر و افزایش responsiveness API.
- Event/Listener برای decoupling جریان‌های تجاری.
- Policies/Gates برای authorization دقیق و قابل نگهداری.
- Cache layer برای کاهش load دیتابیس و بهبود latency.
- Scheduler برای taskهای دوره‌ای با monitoring مناسب.
- Horizon برای مانیتورینگ queue workerها مفید است.
- transaction + dispatch timing باید دقیق باشد (بعد از commit).

## نکات مصاحبه‌ای
- دقیقا توضیح بده چرا کاری را sync یا async کرده‌ای.
- درباره fail/retry behavior و idempotency شفاف باش.

## تمرین سریع
- یک workflow سفارش با Job chain + retry + notification طراحی کن.
