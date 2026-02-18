<div dir="rtl" align="right">
پاسخ‌های کامل سوالات Docker + Kubernetes (Go)

بخش پایه

1) multi-stage build چیست و چرا مهم است؟
پاسخ:
- در چند مرحله image می‌سازی: build stage و runtime stage.
- خروجی نهایی فقط binary و dependency ضروری را دارد.
- حجم image کم می‌شود، سطح حمله امنیتی کمتر می‌شود، pull/deploy سریع‌تر می‌شود.
- برای Go معمولا build در golang image و اجرا در distroless/alpine انجام می‌شود.

2) تفاوت container و VM چیست؟
پاسخ:
- VM کرنل جدا دارد؛ container کرنل host را share می‌کند.
- container سبک‌تر و سریع‌تر بالا می‌آید.
- isolation VM قوی‌تر است، اما هزینه resource بیشتر دارد.
- در production معمولا container روی VM یا managed node اجرا می‌شود.

3) readiness و liveness probe چه فرقی دارند؟
پاسخ:
- readiness: آیا pod آماده دریافت ترافیک است؟
- liveness: آیا process زنده است یا باید restart شود؟
- تنظیم اشتباه readiness باعث ارسال ترافیک به pod ناپایدار می‌شود.
- تنظیم اشتباه liveness می‌تواند restart loop ایجاد کند.

بخش متوسط

1) چرا pod وارد CrashLoopBackOff می‌شود؟
پاسخ:
- process اصلی crash می‌کند یا health probe مدام fail می‌شود.
- علت‌های رایج: config/env اشتباه، dependency unavailable، OOM، migration ناسازگار.
- مسیر تحلیل: `kubectl logs --previous`، describe pod، events، probe config.
- سپس fix مرحله‌ای با rollout کنترل‌شده.

2) requests/limits را چطور تعیین می‌کنی؟
پاسخ:
- از baseline متریک واقعی (CPU/memory p95) شروع می‌کنم.
- requests نزدیک مصرف معمول، limits کمی بالاتر برای spike منطقی.
- limits خیلی تنگ باعث throttling/OOM، خیلی باز باعث noisy-neighbor می‌شود.
- بازبینی دوره‌ای بعد از تغییر traffic/profile لازم است.

3) چگونه secret management را امن انجام می‌دهی؟
پاسخ:
- secret در git plain نگهداری نمی‌شود؛ از secret manager یا encrypted secret استفاده می‌شود.
- least privilege روی service account و namespace.
- rotation دوره‌ای و audit access.
- log/redaction برای جلوگیری از نشت accidental.

4) rolling update را چطور بدون downtime اجرا می‌کنی؟
پاسخ:
- readiness probe صحیح + maxUnavailable پایین + maxSurge کنترل‌شده.
- قبل deploy، backward compatibility API/schema رعایت شود.
- canary درصدی برای سرویس حساس.
- post-deploy metric check و rollback خودکار/دستی آماده.

بخش پیشرفته

1) چگونه هزینه زیرساخت را در K8s کاهش می‌دهی بدون افت پایداری؟
پاسخ:
- right-sizing منابع بر اساس usage واقعی.
- autoscaling هوشمند (HPA/VPA با guardrail).
- workload schedule (spot/preemptible) برای سرویس non-critical.
- image بهینه، cache build، و consolidation nodeها.

2) چه زمانی autoscaling باعث بدتر شدن latency می‌شود؟
پاسخ:
- cold start زیاد باشد (init سنگین، connection warmup).
- metric scaling دیر واکنش بدهد (lag).
- dependency پایین‌دستی ظرفیت scale نداشته باشد.
- راهکار: pre-scale، queue buffer، warm pool.

3) برای stateful workload چه الگوی deployment مناسب است؟
پاسخ:
- StatefulSet با identity و storage پایدار.
- rolling policy محتاطانه و quorum-aware.
- backup/restore تست‌شده و anti-affinity برای HA.
- برای state حیاتی، managed service often safer است.

4) در incident تولید، قدم‌به‌قدم چه چیزهایی را چک می‌کنی؟
پاسخ:
- scope impact (کدام endpoint/region/tenant).
- health metrics: error-rate, latency, saturation.
- recent deploy/config change.
- logs/events/traces و سپس mitigation سریع (rollback/traffic shift) و RCA.
</div>
