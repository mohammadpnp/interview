<div dir="rtl" align="right">
# CI/CD + Release Engineering Notes (Go)

## هدف
آمادگی برای مصاحبه‌هایی که روی تحویل پایدار و سریع تمرکز دارند.

## مباحث کلیدی
- pipeline استاندارد: lint -> unit test -> integration -> build -> scan -> deploy.
- quality gate باید قبل از merge/release enforce شود.
- release strategy: rolling, blue/green, canary.
- feature flag برای کاهش ریسک deploy مفید است.
- artifact باید immutable و traceable باشد.
- rollback باید سریع و تمرین‌شده باشد.
- post-deploy checks: health, SLO, error budget.

## نکات مصاحبه‌ای
- درباره Lead Time, MTTR, Change Failure Rate صحبت کن.
- سرعت release نباید reliability را قربانی کند.

## تمرین سریع
- یک pipeline برای Go service بنویس با canary release و auto rollback.
</div>
