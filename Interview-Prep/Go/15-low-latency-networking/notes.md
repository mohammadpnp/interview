# Low-Latency + Networking Notes (Go)

## هدف
پوشش سوالات latency-sensitive backend (TCP/UDP/WebSocket) در مصاحبه.

## مباحث کلیدی
- budget latency را بین network, compute, storage تقسیم کن.
- connection pooling و keepalive روی latency اثر مستقیم دارد.
- برای realtime، WebSocket یا gRPC stream می‌تواند بهتر از polling باشد.
- timeout/retry باید با awareness شبکه تنظیم شود.
- serialization format (JSON/Proto) روی هزینه CPU/شبکه موثر است.
- backpressure برای جلوگیری از overload ضروری است.
- profiling هم‌زمان CPU/memory/network لازم است.

## نکات مصاحبه‌ای
- با اعداد تقریبی صحبت کن (مثلا p95 هدف، QPS، payload size).
- latency را جدا از throughput تحلیل کن.

## تمرین سریع
- یک endpoint realtime را از REST polling به streaming ارتقا بده و benchmark بگیر.
