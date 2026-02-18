<div dir="rtl" align="right">
# Elasticsearch Notes (PHP Track)

## هدف
پوشش سوالات جستجو و فیلترینگ پیشرفته در سرویس‌های Laravel.

## مباحث کلیدی
- ES برای search/read workload عالی است، منبع truth اصلی نیست.
- mapping مناسب برای فیلدهای قابل فیلتر و sort حیاتی است.
- full-text search با analyzer مناسب کیفیت نتایج را تعیین می‌کند.
- sync strategy بین DB و ES باید قابل بازیابی باشد.
- از alias برای switch index هنگام reindex بدون downtime استفاده کن.
- query profiling در ES برای latency tuning مهم است.

## نکات مصاحبه‌ای
- تفاوت search use-case و transactional use-case را شفاف بگو.
- fallback behavior هنگام اختلال ES را توضیح بده.

## تمرین سریع
- جستجوی محصول با autocomplete + facet filter پیاده‌سازی کن.
</div>
