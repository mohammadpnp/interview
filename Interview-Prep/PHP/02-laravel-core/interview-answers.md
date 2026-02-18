<div dir="rtl" align="right">
پاسخ‌های کامل سوالات Laravel Core

بخش پایه

1) Service Container در Laravel چه می‌کند؟
پاسخ:
- IoC container برای resolve وابستگی‌ها و binding abstraction->implementation.
- lifecycle object و dependency graph را مدیریت می‌کند.
- testability را با امکان جایگزینی fake/mock بالا می‌برد.
- معماری را از new کردن مستقیم جدا می‌کند.

2) تفاوت middleware و policy چیست؟
پاسخ:
- middleware برای concern عمومی درخواست (auth, rate-limit, logging).
- policy برای authorization روی resource/action خاص.
- middleware در مرز request، policy نزدیک domain action.
- ترکیب درست هر دو امنیت و خوانایی را بالا می‌برد.

3) migration چرا مهم است؟
پاسخ:
- schema به‌صورت version-controlled و تکرارپذیر مدیریت می‌شود.
- همسانی محیط dev/stage/prod حفظ می‌شود.
- rollback کنترل‌شده ممکن می‌شود.
- از تغییر دستی و drift جلوگیری می‌کند.

4) Eager Loading چیست؟
پاسخ:
- preload روابط برای جلوگیری از N+1 query.
- تعداد query را کاهش می‌دهد و latency را بهتر می‌کند.
- باید فقط روابط لازم load شوند تا memory بیهوده مصرف نشود.
- در endpointهای list بسیار حیاتی است.

بخش متوسط

1) چگونه N+1 query را تشخیص و رفع می‌کنی؟
پاسخ:
- با query log/APM تعداد query per request را می‌بینم.
- الگوی parent + per-item query را پیدا می‌کنم.
- با eager loading، join یا batching رفع می‌کنم.
- بعد از اصلاح، performance test قبل/بعد می‌گیرم.

2) چه زمانی از Repository در Laravel استفاده می‌کنی؟
پاسخ:
- وقتی domain پیچیده و نیاز به abstraction پایدار از persistence داریم.
- برای جلوگیری از وابستگی مستقیم لایه بالا به ORM جزئیات.
- اگر فقط pass-through CRUD باشد، repository اضافی است.
- باید به زبان domain طراحی شود نه mirror کامل Eloquent.

3) ساختار مناسب برای validation پیچیده چیست؟
پاسخ:
- validation ورودی در FormRequest.
- ruleهای business پیچیده در service/domain validator.
- پیام خطا استاندارد و قابل‌فهم برای کلاینت.
- validation باید deterministic و قابل‌تست باشد.

4) چگونه error response استاندارد API می‌سازی؟
پاسخ:
- schema یکنواخت مثل `{code,message,details,trace_id}`.
- mapping exceptionها به HTTP status مشخص.
- عدم نشت اطلاعات حساس داخلی.
- مستندسازی و contract test برای ثبات پاسخ.

بخش پیشرفته

1) lifecycle request در Laravel را دقیق توضیح بده.
پاسخ:
- درخواست وارد kernel می‌شود، middleware stack اجرا می‌گردد.
- route resolve و controller/action فراخوانی می‌شود.
- dependencyها از container resolve می‌شوند.
- response ساخته و middlewareهای پس‌پردازش اجرا و خروجی ارسال می‌شود.

2) چطور یک ماژول domain-oriented در Laravel طراحی می‌کنی؟
پاسخ:
- ساختار ماژول: Http/Application/Domain/Infrastructure.
- controller thin، use-case orchestration، domain rule مستقل از framework.
- repository interface در domain/application، پیاده‌سازی در infra.
- تست‌های واحد و یکپارچه در مرزهای مشخص.

3) برای پروژه پرترافیک، کدام بخش Laravel bottleneck می‌شود؟
پاسخ:
- بیشتر اوقات DB query و external I/O، نه خود framework.
- N+1، serialization سنگین، session/caching misconfig.
- queue worker ناکافی یا config cache اشتباه.
- profiling واقعی معیار تصمیم است.

4) چه زمانی Eloquent را کنار می‌گذاری و raw query می‌نویسی؟
پاسخ:
- برای queryهای بسیار پیچیده/بهینه که ORM شفافیت کافی ندارد.
- در گزارش‌گیری حجیم یا batch update حساس.
- raw SQL باید parameterized، مستند و تست‌شده باشد.
- ترجیح: اول Eloquent قابل‌فهم، بعد برای hotspot مشخص optimize.
</div>
