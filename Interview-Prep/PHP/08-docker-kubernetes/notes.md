# Docker + Kubernetes Notes (PHP)

## هدف
آمادگی برای deploy و عملیات سرویس‌های Laravel در محیط containerized.

## مباحث کلیدی
- image production را lean بساز (multi-stage + extensionهای لازم).
- config runtime از env/secret تامین شود.
- PHP-FPM + Nginx tuning روی throughput موثر است.
- health check باید کاربردی و سریع باشد.
- در K8s، readiness قبل از اتصال ترافیک تنظیم شود.
- queue workerها scaling جداگانه از web pod داشته باشند.
- rollout strategy + rollback plan همیشه آماده باشد.

## نکات مصاحبه‌ای
- تفاوت scaling web و worker را شفاف توضیح بده.
- مشکلات رایج deploy (cache config, permissions, env mismatch) را بشناس.

## تمرین سریع
- Laravel app + queue worker را با Helm/manifest deploy کن.
