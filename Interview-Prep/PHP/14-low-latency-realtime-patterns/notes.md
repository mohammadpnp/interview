# Low-Latency + Realtime Patterns Notes (PHP)

## هدف
پوشش سوالات realtime و latency-sensitive در سرویس‌های PHP/Laravel.

## مباحث کلیدی
- PHP برای realtime مستقیم محدودیت دارد؛ معماری hybrid رایج است.
- برای realtime می‌توان از WebSocket server جدا یا service جانبی استفاده کرد.
- event broadcasting باید queue-backed و fail-safe باشد.
- cache hot-path برای کاهش latency حیاتی است.
- long-running processها نیازمند memory/leak monitoring هستند.
- API endpointهای حساس باید idempotent و timeout-aware باشند.
- برای بار سنگین، offload به Go service می‌تواند منطقی باشد.

## نکات مصاحبه‌ای
- صادقانه درباره مرز توان PHP صحبت کن و راه‌حل ترکیبی پیشنهاد بده.
- SLA و تجربه کاربر را ملاک انتخاب تکنولوژی قرار بده.

## تمرین سریع
- یک flow اعلان لحظه‌ای با queue + websocket gateway طراحی کن.
