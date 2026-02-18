<div dir="rtl" align="right">
پاسخ‌های کامل سوالات Performance + Security (PHP)

بخش پایه

1) چگونه XSS و SQL injection را در Laravel کنترل می‌کنی؟
پاسخ:
- SQLi: query parameterization و ORM/query builder امن.
- XSS: escaping خروجی و sanitize ورودی‌های لازم.
- validation سمت سرور اجباری است.
- review امنیتی روی نقاط ورودی/نمایش حساس.

2) CSRF چه زمانی فعال است و چرا؟
پاسخ:
- برای درخواست‌های state-changing مبتنی بر session/cookie.
- هدف جلوگیری از request جعلی از سایت ثالث است.
- در API token-based معمولا مکانیزم متفاوت auth داریم.
- misconfig CSRF می‌تواند مسیر حمله باز کند.

3) rate limiting چه مشکلی را حل می‌کند؟
پاسخ:
- جلوگیری از abuse، brute-force، و overload ناگهانی.
- حفظ fairness بین کاربران.
- حفاظت از dependencyهای پایین‌دستی.
- باید با سیاست retry-after و observability همراه باشد.

بخش متوسط

1) bottleneck عملکردی را چگونه پیدا می‌کنی؟
پاسخ:
- APM/profiler برای تفکیک app, DB, external calls.
- slow endpointها و query plan تحلیل می‌شود.
- metricهای p95/p99 و saturation بررسی می‌شود.
- سپس اصلاح اولویت‌دار بر اساس بیشترین impact.

2) چه زمانی cache می‌گذاری و کجا نه؟
پاسخ:
- روی read-heavy و محاسبات گران با tolerance staleness.
- روی داده بسیار حساس به لحظه یا write-heavy ممکن است مضر باشد.
- cache key design و invalidation policy باید روشن باشد.
- cache بدون measurement می‌تواند complexity بی‌اثر بسازد.

3) secretها را چگونه مدیریت می‌کنی؟
پاسخ:
- secret manager/KMS به‌جای hardcode.
- دسترسی حداقلی و rotate دوره‌ای.
- ممنوعیت log کردن secret.
- audit trail برای دسترسی و تغییرات.

4) اگر session hijacking رخ دهد چه اقداماتی داری؟
پاسخ:
- invalidation فوری session/token و forced re-auth.
- بررسی لاگ‌ها برای scope نفوذ.
- rotation secret/cookie config hardening.
- اطلاع‌رسانی و RCA همراه با اقدامات پیشگیرانه.

بخش پیشرفته

1) برای API مالی چه security controls پیشنهاد می‌دهی؟
پاسخ:
- auth قوی (MFA در نقاط حساس)، fine-grained authorization.
- idempotency key، anti-replay، audit immutable.
- rate limit و anomaly detection.
- segregation of duties و approval flow برای عملیات پرریسک.

2) چگونه performance test قابل اعتماد طراحی می‌کنی؟
پاسخ:
- workload واقعی (mix read/write, payload واقعی).
- warm-up + steady-state + spike test.
- معیارهای p95/p99 و error rate.
- محیط نزدیک production و تحلیل bottleneck پس از تست.

3) defense in depth را در backend چگونه اجرا می‌کنی؟
پاسخ:
- لایه شبکه (WAF/firewall)، لایه app (validation/authz)، لایه داده (encryption/access control).
- logging/auditing و alerting چندلایه.
- least privilege همه‌جا.
- assume-breach mindset برای کاهش blast radius.

4) برنامه incident response فنی شما چیست؟
پاسخ:
- detection سریع، incident commander، ارتباطات مشخص.
- containment کوتاه‌مدت (block/rollback/throttle).
- eradication و recovery مرحله‌ای.
- postmortem بدون مقصر با action item قابل پیگیری.
</div>
