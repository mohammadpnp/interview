<div dir="rtl" align="right">
پاسخ‌های کامل سوالات Architecture (DDD + Hexagonal)

بخش پایه

1) Hexagonal Architecture چه مشکلی را حل می‌کند؟
پاسخ:
- منطق دامنه را از فناوری‌های بیرونی (DB/HTTP/Queue) جدا می‌کند.
- تغییر framework یا storage بدون تخریب business logic ممکن می‌شود.
- تست domain سریع‌تر و پایدارتر می‌شود چون وابستگی خارجی mock/fake می‌شود.
- برای تیم‌های بزرگ، boundary روشن باعث کاهش coupling می‌شود.

2) تفاوت Service Layer و Domain Service چیست؟
پاسخ:
- Service Layer (application): orchestrate می‌کند، transaction/call sequence را مدیریت می‌کند.
- Domain Service: قاعده بیزنسی خالصی که متعلق به یک entity نیست.
- anti-pattern: قراردادن business rule در controller/service بیرونی.
- اصل: policy در domain، workflow در application.

3) Entity و Value Object چه تفاوتی دارند؟
پاسخ:
- Entity هویت پایدار دارد (ID) و بر اساس identity مقایسه می‌شود.
- Value Object بی‌هویت و immutable ترجیحی است و بر اساس مقدار مقایسه می‌شود.
- VO برای مدل‌سازی دقیق مفاهیم (Money, Email, Address) خطا را کم می‌کند.
- Entity باید رفتار داشته باشد نه فقط data holder.

بخش متوسط

1) چگونه aggregate boundary را تعیین می‌کنی؟
پاسخ:
- با نگاه به invariantهایی که باید اتمیک حفظ شوند.
- هرجا transaction cross-object زیاد شد، مرز aggregate احتمالا اشتباه است.
- aggregate باید کوچک بماند تا contention و lock کاهش یابد.
- consistency بین aggregateها معمولا eventual و با event انجام می‌شود.

2) repository pattern چه زمانی مفید و چه زمانی اضافی است؟
پاسخ:
- مفید وقتی می‌خواهی domain را از ORM/driver جدا کنی و testable کنی.
- اضافی وقتی صرفا pass-through CRUD می‌سازد و ارزش abstraction ندارد.
- repository باید زبان domain داشته باشد، نه mirror کامل SQL API.
- over-abstract کردن query پیچیده می‌تواند performance/debug را بدتر کند.

3) dependency inversion را در Go چگونه پیاده می‌کنی؟
پاسخ:
- interface در لایه مصرف‌کننده تعریف می‌شود.
- implementation در adapter پایین‌دستی قرار می‌گیرد.
- wiring در composition root (main/bootstrap) انجام می‌شود.
- domain package هیچ import از framework/infra ندارد.

4) چطور از leakage منطق بیزنسی به handler جلوگیری می‌کنی؟
پاسخ:
- handler فقط parse/validate ابتدایی/response mapping انجام دهد.
- use-case در application service فراخوانی شود.
- ruleها در entity/domain service enforce شوند.
- code review rule: business if/else در transport layer ممنوع.

بخش پیشرفته

1) migration از monolith به architecture ماژولار را چگونه مرحله‌بندی می‌کنی؟
پاسخ:
- مرحله 1: شناسایی bounded contextهای پرریسک.
- مرحله 2: استخراج interface و anti-corruption layer.
- مرحله 3: جابه‌جایی تدریجی use-caseها با contract test.
- مرحله 4: مشاهده‌پذیری/rollback plan برای هر گام، سپس حذف مسیر قدیمی.

2) چگونه consistency بین چند aggregate را مدیریت می‌کنی؟
پاسخ:
- strong consistency فقط جایی که حیاتی است و هزینه‌اش توجیه دارد.
- برای بقیه، domain event + saga/process manager و جبران (compensation).
- idempotency و ordering strategy ضروری است.
- مانیتورینگ mismatch و reconciliation job باید داشته باشی.

3) در چه شرایطی event-driven domain مناسب‌تر است؟
پاسخ:
- وقتی چند bounded context مستقل باید به تغییرات واکنش دهند.
- وقتی throughput بالا و decoupling اهمیت دارد.
- وقتی latency غیرهمزمان قابل‌قبول است.
- اگر تیم تجربه کم دارد یا نیاز شدید به تراکنش لحظه‌ای دارد، شروع با sync ساده‌تر است.

4) یک نمونه anti-corruption layer واقعی توضیح بده.
پاسخ:
- فرض کن سیستم legacy مالی فیلدهای مبهم دارد. ACL تبدیل می‌کند به مدل شفاف domain جدید.
- mapping خطاها، تبدیل enumها، نرمال‌سازی زمان/واحد پول در ACL انجام می‌شود.
- domain جدید هیچ دانشی از weirdness legacy ندارد.
- نتیجه: مهاجرت امن‌تر و جلوگیری از نشت مفاهیم ناسالم قدیمی.
</div>
