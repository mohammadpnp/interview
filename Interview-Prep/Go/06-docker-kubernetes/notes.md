<div dir="rtl" align="right">
# Docker + Kubernetes Notes (Go)

## هدف
آمادگی برای سوالات عملی Deployment، Runtime، و سلامت سرویس‌ها.

## مباحث کلیدی
- Docker image باید کوچک، reproducible و امن باشد (multi-stage build).
- environment parity: تفاوت dev/staging/prod را کنترل کن.
- در Kubernetes، `Deployment` برای stateless و `StatefulSet` برای stateful.
- `readinessProbe` برای دریافت ترافیک، `livenessProbe` برای restart.
- resource requests/limits برای جلوگیری از noisy neighbor لازم است.
- config از طریق ConfigMap/Secret، نه hardcode.
- rolling update + rollback strategy باید از قبل تعریف شود.

## نکات مصاحبه‌ای
- علت CrashLoopBackOff را مرحله‌ای تحلیل کن (logs, probe, config, resource).
- observability بعد از deploy را بخشی از پاسخ قرار بده.

## تمرین سریع
- یک Dockerfile چندمرحله‌ای برای Go app بنویس و در K8s deploy کن.
</div>
