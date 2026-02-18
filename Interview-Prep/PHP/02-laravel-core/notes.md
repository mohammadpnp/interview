# Laravel Core Notes

## هدف
پاسخ حرفه‌ای به سوالات پایه Laravel در مصاحبه Backend.

## مباحث کلیدی
- Service Container هسته DI در Laravel است.
- Service Providerها محل registration bindingها هستند.
- Eloquent قدرتمند است ولی باید از N+1 و query سنگین جلوگیری کرد.
- Middleware برای cross-cutting concern مثل auth/logging/rate-limit.
- Validation باید نزدیک مرز ورودی (FormRequest) انجام شود.
- Config و env management باید امن و محیط‌محور باشد.
- Migrationها باید قابل rollback و بدون ریسک باشند.

## نکات مصاحبه‌ای
- معماری تمیز در Laravel یعنی جداکردن Controller از منطق بیزنسی.
- برای هر انتخاب Eloquent/raw query دلیل روشن داشته باش.

## تمرین سریع
- یک endpoint CRUD با validation، policy و pagination تمیز بساز.
