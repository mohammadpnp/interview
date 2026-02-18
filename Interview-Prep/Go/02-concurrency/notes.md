<div dir="rtl" align="right">
# Concurrency Notes (Go)

## هدف
پاسخ‌گویی قوی به سوالات goroutine/channel/sync و طراحی concurrent-safe.

## مباحث کلیدی
- برای cancellation از `context` استفاده کن، نه channel سفارشی پراکنده.
- `unbuffered channel` برای handoff مستقیم؛ `buffered` برای decoupling producer/consumer.
- الگوهای مهم: worker pool، fan-in/fan-out، pipeline.
- race condition را با `go test -race` و طراحی immutable/lock-based کنترل کن.
- `sync.Mutex` ساده‌ترین گزینه است؛ قبل از پیچیده کردن راه‌حل، lock contention را اندازه بگیر.
- از goroutine leak با timeout/cancel و بستن درست channel جلوگیری کن.
- `select` برای timeout، cancellation و multiplexing کانال‌ها ضروری است.

## خطاهای پرتکرار
- بستن channel از سمت receiver
- فراموشی `wg.Done()`
- ارسال روی channel بسته
- shared map بدون lock

## تمرین سریع
- worker pool بنویس با context cancellation و retry محدود.
</div>
