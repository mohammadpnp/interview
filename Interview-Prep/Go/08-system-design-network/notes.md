<div dir="rtl" align="right">
# System Design + Network Notes (Go)

## هدف
آمادگی برای طراحی سرویس مقیاس‌پذیر، پایدار، و قابل نگهداری.

## مباحث کلیدی
- ابتدا نیازمندی‌ها: QPS، latency target، consistency، availability.
- load balancer + stateless service + cache + DB pattern پایه است.
- CAP و trade-offها را با سناریوی واقعی توضیح بده.
- idempotency برای endpointهای مالی/پرداخت حیاتی است.
- timeout, retry, backoff, circuit breaker باید هماهنگ طراحی شوند.
- TCP basics: handshake، keepalive، connection pooling روی latency اثر دارد.
- queue-based async processing برای workload سنگین مناسب است.

## نکات مصاحبه‌ای
- معماری را مرحله‌بندی کن: MVP سپس scale plan.
- bottleneck بعدی را پیش‌بینی و instrumentation تعریف کن.

## تمرین سریع
- طراحی high-level برای سفارش‌گیری با 50k RPM و SLA مشخص.
</div>
