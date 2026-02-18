<div dir="rtl" align="right">
پاسخ‌های کامل سوالات PHP Core + OOP

بخش پایه

1) تفاوت == و === چیست؟
پاسخ:
- `==` مقایسه با تبدیل نوع (type juggling) انجام می‌دهد.
- `===` هم مقدار و هم نوع را دقیق مقایسه می‌کند.
- در کد production، برای جلوگیری از bugهای پنهان ترجیح با `===` است.
- نمونه خطر: `'0' == false` درست می‌شود ولی با `===` نادرست است.

2) static method چه زمانی مناسب است؟
پاسخ:
- وقتی behavior بدون state instance است (helper pure یا factory محدود).
- برای utilityهای پایدار و بدون وابستگی.
- استفاده زیاد از static، تست‌پذیری و DI را خراب می‌کند.
- business logic اصلی بهتر است در instance service با DI باشد.

3) trait در PHP چه کاربردی دارد؟
پاسخ:
- reuse رفتار مشترک بین کلاس‌های نامرتبط.
- برای cross-cutting behavior کوچک مفید است.
- سوءاستفاده از trait می‌تواند coupling پنهان بسازد.
- اگر trait بزرگ شد، احتمالا باید به service جدا refactor شود.

4) namespace چه مشکلی را حل می‌کند؟
پاسخ:
- جلوگیری از برخورد نام کلاس/تابع در پروژه بزرگ.
- سازمان‌دهی منطقی کد براساس domain/module.
- هماهنگ با PSR-4 autoloading.
- خوانایی و نگهداری پروژه را بالا می‌برد.

بخش متوسط

1) چگونه SOLID را در پروژه واقعی Laravel رعایت می‌کنی؟
پاسخ:
- SRP: controller نازک، logic در service/use-case.
- OCP: رفتار جدید با interface/strategy اضافه می‌شود نه if-else زنجیره‌ای.
- LSP/ISP: interfaceهای کوچک و قابل‌جایگزینی.
- DIP: وابستگی به abstraction و binding در container.

2) dependency injection چه مزیتی دارد؟
پاسخ:
- coupling را کم می‌کند و تست‌پذیری را بالا می‌برد.
- جایگزینی implementation بدون تغییر consumer.
- wiring وابستگی‌ها متمرکز و قابل‌مشاهده می‌شود.
- در Laravel container این کار را ساده می‌کند.

3) exception handling مناسب در لایه service چگونه است؟
پاسخ:
- خطاهای فنی و business را تفکیک کن.
- در service خطا را contextualize کن، در مرز API به response استاندارد map کن.
- نشت stack داخلی به کاربر ممنوع.
- logging ساخت‌یافته + trace id برای debugging ضروری است.

4) چه زمانی inheritance بدتر از composition است؟
پاسخ:
- وقتی سلسله‌مراتب مصنوعی و شکننده می‌سازد.
- تغییر در base class اثر جانبی گسترده ایجاد می‌کند.
- composition انعطاف و تست بهتر می‌دهد.
- inheritance فقط برای «is-a» واقعی و پایدار مناسب است.

بخش پیشرفته

1) یک نمونه طراحی ضعیف OOP را refactor کن.
پاسخ:
- نمونه: God class با 2000 خط که validation+DB+notification را باهم دارد.
- refactor: extract serviceها، interface تعریف، orchestration در use-case.
- نتیجه: unit test سریع‌تر، تغییرات ایزوله، review ساده‌تر.
- معیار موفقیت: کاهش coupling و کاهش defect بعد release.

2) چگونه coupling بین moduleها را کاهش می‌دهی؟
پاسخ:
- قرارداد روشن بین moduleها (DTO/interface/event).
- حذف import مستقیم از لایه‌های نامرتبط.
- anti-corruption layer برای سیستم legacy.
- enforcement با architecture lint/code review.

3) برای legacy PHP codebase چه strategy بهبود تدریجی داری؟
پاسخ:
- strangler pattern: feature جدید بیرون از legacy و route تدریجی.
- characterization tests قبل refactor.
- ماژول‌بندی گام‌به‌گام و معیارهای کیفیت.
- هر تغییر کوچک deployable و rollbackable بماند.

4) چگونه backward compatibility را در releaseهای پیوسته حفظ می‌کنی؟
پاسخ:
- قرارداد API versioned و deprecation policy.
- expand-contract در DB migration.
- feature flag برای rollout تدریجی.
- contract test بین producer/consumer.
</div>
