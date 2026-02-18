<div dir="rtl" align="right">
# Go Core Notes

## هدف
تسلط روی مفاهیم پایه Go که در مصاحبه سطح Mid/Senior به‌صورت عمیق پرسیده می‌شوند.

## مباحث کلیدی
- `goroutine` سبک است، اما بی‌نهایت نیست؛ مدیریت lifecycle مهم است.
- `interface` باید کوچک و مبتنی بر رفتار باشد (`io.Reader` style).
- `pointer receiver` زمانی مناسب است که state تغییر می‌کند یا struct بزرگ است.
- `zero value` در Go مهم است؛ طراحی API باید با zero-value-friendly بودن هماهنگ باشد.
- خطا در Go باید wrap شود (`fmt.Errorf("...: %w", err)`) تا context از بین نرود.
- `context.Context` برای cancellation/timeout/request-scope data استفاده می‌شود.
- تفاوت `new(T)` و `make(...)`: اولی allocation نوع، دومی initialization برای map/slice/channel.
- map در Go thread-safe نیست و برای concurrent access باید lock/sync.Map داشته باشید.

## نکات مصاحبه‌ای
- از Generic فقط وقتی استفاده کن که duplication واقعی وجود دارد.
- در APIها، error message کاربرپسند + log detail جداگانه نگه دار.
- import cycle نداشته باش؛ boundary پکیج‌ها را روشن کن.

## تمرین سریع
- یک package utility با interface کوچک و تست unit بنویس.
- یک refactor انجام بده که panicهای غیرضروری را به error return تبدیل کند.
</div>
