# Concurrency Interview Questions

## پایه
1. goroutine چیست و با thread چه تفاوتی دارد؟
2. تفاوت channel با mutex در چیست؟
3. buffered vs unbuffered channel را با مثال توضیح بده.
4. چه کسی باید channel را close کند؟

## متوسط
1. race condition چیست و چطور تشخیص می‌دهی؟
2. deadlock رایج در Go چیست؟
3. چگونه worker pool پیاده می‌کنی؟
4. چه زمانی `RWMutex` بهتر از `Mutex` است؟
5. چرا استفاده بی‌رویه از goroutine خطرناک است؟

## پیشرفته
1. چگونه از goroutine leak در long-running service جلوگیری می‌کنی؟
2. یک pipeline concurrent طراحی کن که backpressure داشته باشد.
3. چگونه graceful shutdown برای چند goroutine هم‌زمان می‌سازی؟
4. سناریویی بگو که lock-free approach مناسب‌تر از mutex باشد.
5. چگونه latency tail را در workload concurrent کاهش می‌دهی؟
