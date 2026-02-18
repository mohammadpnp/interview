# Testing + Observability Notes (Go)

## هدف
اثبات توانایی ساخت سرویس قابل اعتماد با تست و مانیتورینگ مؤثر.

## مباحث کلیدی
- تست‌ها: Unit (سریع)، Integration (واقعی‌تر)، E2E (مسیر کامل).
- table-driven test در Go باعث پوشش بهتر سناریوها می‌شود.
- mock فقط برای dependencyهای بیرونی؛ از over-mocking پرهیز کن.
- برای flaky test: time dependency، race، shared state را حذف کن.
- logging ساخت‌یافته + correlation id ضروری است.
- metrics اصلی: latency (p95/p99)، error rate، throughput، saturation.
- tracing برای یافتن bottleneck بین سرویس‌ها بسیار مفید است.

## نکات مصاحبه‌ای
- نشان بده تست را ابزار طراحی می‌بینی، نه فقط پوشش درصدی.
- درباره SLI/SLO در سرویس‌های کلیدی صحبت کن.

## تمرین سریع
- برای یک endpoint، unit + integration + benchmark بنویس.
