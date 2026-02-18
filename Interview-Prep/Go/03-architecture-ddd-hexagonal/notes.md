<div dir="rtl" align="right">
# Architecture Notes (DDD + Hexagonal)

## هدف
توانایی دفاع از طراحی سیستم با boundaryهای واضح و تست‌پذیری بالا.

## مباحث کلیدی
- Hexagonal: domain در مرکز، adapterها در لبه (DB, HTTP, Queue).
- DDD: Entity، Value Object، Aggregate، Domain Service، Repository.
- application service orchestration می‌کند؛ business rule داخل domain می‌ماند.
- aggregate باید invariantها را حفظ کند؛ transaction boundary معمولاً aggregate است.
- anti-corruption layer برای اتصال domain داخلی به سیستم خارجی مفید است.
- dependency inversion: domain نباید به framework وابسته باشد.

## نکات مصاحبه‌ای
- over-engineering نکن: DDD کامل برای هر پروژه لازم نیست.
- اول domainهای پرریسک/پیچیده را modular کن.
- naming و ubiquitous language بسیار مهم است.

## تمرین سریع
- یک use-case سفارش را با application service + repository interface مدل کن.
</div>
