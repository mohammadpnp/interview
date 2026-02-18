<div dir="rtl" align="right">
پاسخ‌های کامل سوالات Docker + Kubernetes (PHP)

بخش پایه

1) چرا multi-stage build برای PHP مفید است؟
پاسخ:
- ابزار build و dependency توسعه از image نهایی حذف می‌شود.
- image کوچک‌تر و امن‌تر می‌شود.
- deploy/pull سریع‌تر می‌شود.
- کنترل بهتری روی extensionها و runtime دارید.

2) readiness و liveness در Laravel چه endpointی داشته باشند؟
پاسخ:
- readiness: بررسی اتصال‌های حیاتی (DB/Redis) و آمادگی app.
- liveness: بررسی سبک برای زنده بودن process.
- readiness نباید خیلی سنگین باشد.
- health endpoint باید قابل‌اعتماد و سریع باشد.

3) تفاوت pod web و pod worker چیست؟
پاسخ:
- web pod درخواست HTTP را پاسخ می‌دهد.
- worker pod jobهای queue را پردازش می‌کند.
- scaling و resource profile این دو متفاوت است.
- failure mode و monitoring آن‌ها نیز جداگانه تعریف می‌شود.

بخش متوسط

1) چگونه zero-downtime deploy انجام می‌دهی؟
پاسخ:
- rolling/canary deployment با readiness درست.
- version سازگار با schema migration.
- pre/post deploy check و rollback plan.
- session/cache compatibility بین نسخه‌ها رعایت شود.

2) config cache در Laravel چه تاثیری روی deployment دارد؟
پاسخ:
- startup سریع‌تر و کاهش overhead runtime.
- اگر env درست inject نشود، خطای پنهان ایجاد می‌کند.
- باید در pipeline مرحله build/release واضح باشد.
- invalidate صحیح cache در release ضروری است.

3) چگونه resource limit مناسب تعیین می‌کنی؟
پاسخ:
- از متریک واقعی CPU/memory و profile traffic شروع می‌کنم.
- requests بر اساس مصرف پایدار، limits کمی بالاتر.
- برای worker memory leak patterns را جدا پایش می‌کنم.
- بازتنظیم دوره‌ای با رشد بار.

4) چه زمانی queue worker باید autoscale شود؟
پاسخ:
- وقتی lag یا age پیام از threshold عبور کند.
- metricمحور (queue depth, processing latency).
- سقف scale برای حفاظت از DB/dependency.
- cooldown برای جلوگیری از oscillation.

بخش پیشرفته

1) اگر بعد از deploy نرخ خطا بالا رفت، روند triage چیست؟
پاسخ:
- تعیین scope و endpointهای متاثر.
- بررسی تغییرات اخیر code/config.
- logs/traces و dependency health.
- rollback سریع اگر impact بالا باشد، سپس RCA.

2) چگونه هزینه زیرساخت PHP را بهینه می‌کنی؟
پاسخ:
- right-sizing podها و autoscaling هدفمند.
- بهینه‌سازی opcache و PHP-FPM config.
- cache موثر برای کاهش load DB.
- حذف resource هدررفته و schedule هوشمند.

3) چه زمانی سرویس را از PHP به Go جدا می‌کنی؟
پاسخ:
- وقتی نیاز latency/concurrency فراتر از هزینه نگهداری در PHP باشد.
- hotspot مشخص و measurable باشد.
- مرز domain واضح برای extraction.
- migration تدریجی با contract پایدار.

4) در rollout ناقص، rollback safe چطور انجام می‌دهی؟
پاسخ:
- بازگشت سریع به نسخه پایدار آخر.
- تضمین سازگاری schema (expand-contract).
- پاکسازی کارهای نیمه‌تمام با idempotent cleanup.
- verify پس از rollback و freeze تغییرات تا تحلیل کامل.
</div>
