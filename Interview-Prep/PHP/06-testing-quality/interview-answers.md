<div dir="rtl" align="right">
پاسخ‌های کامل سوالات Testing + Quality (PHP)

بخش پایه

1) تفاوت unit و feature test در Laravel چیست؟
پاسخ:
- unit test منطق کوچک و isolated را بررسی می‌کند.
- feature test رفتار endpoint/flow را با framework integration می‌سنجد.
- unit سریع‌تر، feature نزدیک‌تر به واقعیت است.
- هر دو برای پوشش ریسک‌های متفاوت لازم‌اند.

2) mock چه زمانی لازم است؟
پاسخ:
- برای dependency بیرونی کند/ناپایدار (API, queue, email).
- برای جداسازی behavior واحد در unit test.
- over-mock تست را brittle می‌کند.
- fakeهای ساده گاهی پایدارتر از mock پیچیده هستند.

3) چرا تست‌ها flaky می‌شوند؟
پاسخ:
- shared state، زمان/تاریخ واقعی، race condition.
- وابستگی شبکه/DB غیرایزوله.
- ترتیب اجرا یا data cleanup ناقص.
- راه‌حل: isolation کامل، deterministic setup/teardown.

بخش متوسط

1) چگونه CI pipeline تست را سریع نگه می‌داری؟
پاسخ:
- split کردن suiteها و parallel execution.
- unitها جدا و سریع، integration محدود اما هدفمند.
- test data setup بهینه و cache dependency.
- quarantine flaky test تا رفع ریشه‌ای.

2) آیا coverage بالا همیشه خوب است؟
پاسخ:
- نه؛ coverage فقط execution را نشان می‌دهد نه کیفیت assertion.
- ممکن است edge case مهم تست نشده باشد.
- coverage را signal می‌گیریم نه هدف نهایی.
- معیار اصلی: کاهش bug تولیدی و confidence release.

3) برای APIها چه نوع testهایی ضروری‌ترند؟
پاسخ:
- contract/feature test برای schema و status code.
- integration test برای DB/business workflow.
- security test حداقلی برای auth/rate limit/validation.
- smoke test پس از deploy.

4) static analysis چه ارزشی دارد؟
پاسخ:
- خطاهای type/nullable و anti-pattern را قبل runtime می‌گیرد.
- quality baseline تیمی ایجاد می‌کند.
- review را روی منطق مهم متمرکز می‌کند.
- باید با سطح strict تدریجی پیاده شود.

بخش پیشرفته

1) strategy تست برای refactor بزرگ چیست؟
پاسخ:
- characterization tests برای تثبیت رفتار فعلی.
- refactor تدریجی با branchهای کوچک و deploy امن.
- contract tests برای جلوگیری از breaking change.
- monitor production metric برای regression پنهان.

2) اگر test suite خیلی کند شد چه می‌کنی؟
پاسخ:
- profiling suite و شناسایی slowest tests.
- حذف dependency واقعی از unit tests.
- parallelism کنترل‌شده و data fixture lightweight.
- بازطراحی تست‌های کم‌ارزش و تکراری.

3) contract testing در microserviceها چه جایگاهی دارد؟
پاسخ:
- تضمین همخوانی producer/consumer بدون نیاز E2E کامل.
- شکست زودهنگام breaking contract در CI.
- برای API/event هر دو مفید است.
- هزینه نگهداری دارد ولی outage را کم می‌کند.

4) چگونه quality gate قابل اعتماد تعریف می‌کنی؟
پاسخ:
- gateها محدود، شفاف و پایدار باشند.
- شامل lint, unit test, critical integration, security baseline.
- false positive کم و زمان اجرای قابل‌قبول.
- exception process مستند و traceable باشد.
</div>
