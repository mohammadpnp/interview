<div dir="rtl" align="right">
# Database Notes (MySQL/PostgreSQL + Redis)

## هدف
مدیریت داده قابل اعتماد و سریع در پروژه‌های Laravel/PHP.

## مباحث کلیدی
- schema design باید متناسب با query pattern انجام شود.
- index composite را براساس where/order واقعی بساز.
- transaction برای عملیات چندمرحله‌ای حساس اجباری است.
- از locking strategy مناسب (optimistic/pessimistic) استفاده کن.
- Redis برای cache، session، queue و rate limiting مناسب است.
- invalidation strategy مهم‌تر از خود cache است.
- query profiling منظم برای پیشگیری از افت عملکرد لازم است.

## نکات مصاحبه‌ای
- به جای جواب کلی، query و index واقعی مثال بزن.
- اثر هر تصمیم روی write/read cost را بیان کن.

## تمرین سریع
- یک endpoint کند را با index و cache بهبود بده.
</div>
