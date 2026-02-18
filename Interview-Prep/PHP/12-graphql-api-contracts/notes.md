<div dir="rtl" align="right">
# GraphQL + API Contracts Notes (PHP/Laravel)

## هدف
آمادگی برای سوالات GraphQL که کنار REST در بعضی آگهی‌های backend دیده می‌شود.

## مباحث کلیدی
- GraphQL برای کاهش over-fetching و انعطاف کلاینت مفید است.
- resolver design باید کارآمد باشد و N+1 را کنترل کند.
- DataLoader/Batching برای performance ضروری است.
- schema-driven development کیفیت قرارداد API را بالا می‌برد.
- authorization در سطح query/field باید پیاده شود.
- limiting depth/complexity برای امنیت و پایداری لازم است.
- logging/tracing queryها برای tuning ضروری است.

## نکات مصاحبه‌ای
- GraphQL را به‌عنوان مکمل REST معرفی کن، نه همیشه جایگزین.
- از منظر امنیت، caching و monitoring پاسخ بده.

## تمرین سریع
- یک schema برای profile + orders بساز و query پیچیده را optimize کن.
</div>
