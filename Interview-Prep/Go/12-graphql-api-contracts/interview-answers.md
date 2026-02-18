<div dir="rtl" align="right">
پاسخ‌های کامل سوالات GraphQL + API Contracts (Go)

بخش پایه

1) GraphQL چه مزیتی نسبت به REST دارد؟
پاسخ:
- کلاینت دقیقا فیلدهای لازم را می‌گیرد (کاهش over-fetch/under-fetch).
- aggregation چند منبع در یک request ساده‌تر می‌شود.
- schema قوی و self-documenting فراهم می‌کند.
- برای public API ساده، REST هنوز ساده‌تر و operationally راحت‌تر است.

2) schema و resolver چه نقشی دارند؟
پاسخ:
- schema قرارداد داده و عملیات را تعریف می‌کند.
- resolver منطق fetch/compose داده برای هر field/query است.
- کیفیت resolver مستقیما روی latency اثر می‌گذارد.
- schema design باید domain-oriented باشد، نه DB-oriented.

3) مشکل N+1 در GraphQL چیست؟
پاسخ:
- برای هر item یک query جدا به DB/service زده می‌شود.
- latency و load به‌صورت انفجاری رشد می‌کند.
- راه‌حل: DataLoader/batching/caching per request.
- trace و query count برای تشخیص لازم است.

بخش متوسط

1) چگونه query complexity را محدود می‌کنی؟
پاسخ:
- depth limit، field cost model، max nodes/timeout.
- queryهای سنگین block یا نیازمند allowlist می‌شوند.
- برای clientهای trusted quotas جدا تعیین می‌کنم.
- telemetry complexity برای tuning policy استفاده می‌شود.

2) authorization در GraphQL را چگونه پیاده می‌کنی؟
پاسخ:
- auth در لایه ورودی (context user) و authz در resolver/field enforce می‌شود.
- سیاست‌ها role/permission-based و resource-aware هستند.
- عدم دسترسی باید partial-safe handle شود (null یا error policy روشن).
- audit log روی دسترسی‌های حساس ضروری است.

3) چه زمانی REST یا gRPC بهتر از GraphQL است؟
پاسخ:
- REST: endpointهای ساده و کش CDN-friendly.
- gRPC: ارتباط داخلی با کارایی بالا و typed contract.
- GraphQL: aggregation و UI-driven data نیازمند انعطاف.
- معماری hybrid غالبا بهترین trade-off است.

4) API contract governance در تیم چندسرویسی چطور انجام می‌شود؟
پاسخ:
- قراردادها versioned و code-reviewed هستند.
- breaking change policy و deprecation window تعریف می‌شود.
- contract test در CI برای producer/consumer mandatory.
- ownership هر schema/service واضح است.

بخش پیشرفته

1) یک GraphQL gateway برای چند microservice چطور طراحی می‌کنی؟
پاسخ:
- gateway schema federation یا stitched schema ارائه می‌دهد.
- resolverها به سرویس‌های پایین‌دستی route می‌کنند با timeout/circuit-breaker.
- caching و batching در gateway برای کاهش call storm.
- observability دقیق per-field/per-service برای تشخیص bottleneck.

2) چگونه breaking change را در schema مدیریت می‌کنی؟
پاسخ:
- اول deprecate با توضیح migration path.
- نظارت usage clientها، سپس sunset زمان‌بندی‌شده.
- adapter موقت برای backward compatibility.
- تغییر ناگهانی ممنوع مگر incident/security critical.

3) strategy cache در GraphQL چیست؟
پاسخ:
- cache لایه gateway برای queryهای read-heavy.
- per-resolver cache برای dependency گران.
- invalidation event-based + TTL ترکیبی.
- cache key باید شامل identity/permission باشد تا data leak رخ ندهد.

4) اگر یک query سنگین latency را بالا ببرد، روند اصلاح چیست؟
پاسخ:
- trace query plan و resolver timings را می‌گیرم.
- N+1، join سنگین، یا dependency کند را isolate می‌کنم.
- batching, prefetch, complexity limit و schema refactor انجام می‌دهم.
- سپس regression test و alert برای جلوگیری از بازگشت مشکل.
</div>
