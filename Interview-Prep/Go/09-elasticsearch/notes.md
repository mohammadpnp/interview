<div dir="rtl" align="right">
# Elasticsearch Notes (Go Track)

## هدف
تسلط روی مفاهیم جستجو که در مصاحبه شرکت‌های محصول‌محور زیاد پرسیده می‌شود.

## مباحث کلیدی
- Elasticsearch موتور جستجوی full-text است، جایگزین کامل DB رابطه‌ای نیست.
- mapping صحیح برای فیلدها حیاتی است (`text` vs `keyword`).
- analyzer/tokenizer کیفیت نتیجه جستجو را تعیین می‌کند.
- relevance با BM25 و boosting قابل تنظیم است.
- index lifecycle (rollover/retention) برای هزینه و عملکرد مهم است.
- refresh interval روی near-real-time بودن و performance تاثیر می‌گذارد.
- باید strategy برای sync بین DB اصلی و ES داشته باشی (CDC/event/outbox).

## نکات مصاحبه‌ای
- consistency بین source of truth و index جستجو را شفاف توضیح بده.
- درباره reindex و versioning mapping آماده باش.

## تمرین سریع
- یک ایندکس محصول با قابلیت autocomplete و فیلتر قیمت/برند طراحی کن.
</div>
