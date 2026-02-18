<div dir="rtl" align="right">
پاسخ‌های کامل سوالات Cloud + IaC + GitOps (Go)

بخش پایه

1) IaC چه مزایایی نسبت به تنظیمات دستی دارد؟
پاسخ:
- زیرساخت قابل تکرار، reviewable و version-controlled می‌شود.
- خطای انسانی کاهش می‌یابد.
- محیط‌های dev/stage/prod هماهنگ‌تر می‌شوند.
- rollback و audit بسیار ساده‌تر می‌شود.

2) Helm چه مشکلی را حل می‌کند؟
پاسخ:
- template و versioning deployment روی Kubernetes.
- مدیریت مقادیر محیطی (values) بدون تکثیر manifest.
- release history و rollback ساده‌تر.
- استانداردسازی deployment بین تیم‌ها.

3) GitOps به چه معناست؟
پاسخ:
- git منبع حقیقت desired state است.
- controller تغییرات را از git به کلاستر reconcile می‌کند.
- drift detection و rollback از commit history انجام می‌شود.
- امنیت با PR review و policy gate بالاتر می‌رود.

بخش متوسط

1) چگونه drift بین infra واقعی و تعریف IaC را کنترل می‌کنی؟
پاسخ:
- ممنوعیت تغییر دستی مستقیم در محیط production.
- drift detection دوره‌ای و alert.
- reconcile خودکار یا PR اصلاحی.
- محدودسازی permission برای جلوگیری از config drift.

2) rollout امن در Kubernetes چگونه طراحی می‌شود؟
پاسخ:
- health probes دقیق + readiness gate.
- progressive delivery (canary/rolling) با metric guard.
- rollback سریع با معیارهای شکست تعریف‌شده.
- schema/API compatibility قبل rollout بررسی شود.

3) secret management استاندارد چیست؟
پاسخ:
- secret در plaintext در repo ذخیره نمی‌شود.
- ابزارهای امن مثل Vault/KMS/Sealed Secrets.
- rotation، least-privilege و audit access اجباری.
- redaction در log و trace جلوگیری از نشت.

4) چه زمانی self-hosted infra نسبت به cloud managed بهتر است؟
پاسخ:
- نیاز شدید به کنترل سفارشی، هزینه بلندمدت خاص، یا محدودیت قانونی.
- تیم SRE بالغ و ظرفیت عملیاتی 24/7 داشته باشد.
- managed service سرعت delivery و reliability اولیه را بالا می‌برد.
- تصمیم باید TCO + ریسک عملیاتی محور باشد.

بخش پیشرفته

1) یک architecture چندمحیطی (dev/stage/prod) با GitOps طراحی کن.
پاسخ:
- repo ساختاریافته با overlays محیطی.
- promotion flow از dev به stage به prod با PR و approval.
- policy checks (security/lint) قبل merge.
- rollback با revert commit و reconcile خودکار.

2) برای disaster recovery چه RTO/RPO هدف می‌گذاری و چرا؟
پاسخ:
- بر اساس criticality سرویس و هزینه downtime/data loss.
- سرویس مالی: RPO پایین، RTO کوتاه؛ سرویس غیرحیاتی lenientتر.
- backup periodic + restore drill واقعی.
- اهداف DR باید test شوند نه صرفا مستندسازی.

3) چگونه امنیت pipeline زیرساخت را افزایش می‌دهی؟
پاسخ:
- least privilege برای runner/service account.
- امضای artifact، dependency scanning، policy-as-code.
- secret کوتاه‌عمر و OIDC federation.
- audit trail کامل روی تغییرات و اجراها.

4) در outage ناشی از config اشتباه چه runbookی اجرا می‌کنی؟
پاسخ:
- freeze تغییرات جدید، تعیین blast radius.
- rollback سریع به last-known-good.
- verification با health/SLO dashboards.
- RCA با action item: guardrail بیشتر، test config، approval سخت‌گیرانه‌تر.
</div>
