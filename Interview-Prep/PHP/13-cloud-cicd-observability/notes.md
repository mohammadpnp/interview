# Cloud + CI/CD + Observability Notes (PHP)

## هدف
تجمیع مهارت‌های عملیاتی که در آگهی‌های Senior PHP/Laravel پرتکرار هستند.

## مباحث کلیدی
- CI/CD: build/test/scan/deploy با gate مشخص.
- deployment strategy امن: canary یا rolling + rollback سریع.
- monitoring با Prometheus/Grafana و alert هدفمند.
- tracing با OpenTelemetry/Jaeger برای مسیرهای کند.
- SLI/SLO تعریف شود و با error budget مدیریت شود.
- log ساخت‌یافته با correlation id برای debugging سریع.
- cloud cost visibility برای scale واقعی لازم است.

## نکات مصاحبه‌ای
- observability را جزو definition of done در نظر بگیر.
- پاسخ‌ها باید شامل detection + mitigation + prevention باشند.

## تمرین سریع
- برای یک API پرترافیک dashboard مانیتورینگ + alert policy طراحی کن.
