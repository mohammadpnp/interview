# Go Core Interview Questions

## پایه
1. تفاوت `array` و `slice` چیست و impact آن روی performance چطور است؟
2. `defer` چه زمانی اجرا می‌شود و چه هزینه‌ای دارد؟
3. تفاوت `panic` و `error` چیست؟
4. `interface{}` در Go جدید چه جایگزین‌هایی دارد؟
5. `init()` چه زمانی مناسب است و چه زمانی ضدالگو است؟

## متوسط
1. چه زمانی `pointer receiver` بهتر از `value receiver` است؟
2. چگونه wrapping error به debugging کمک می‌کند؟
3. design یک package تمیز در Go چه اصولی دارد؟
4. چگونه از import cycle جلوگیری می‌کنید؟
5. تفاوت `nil slice` و `empty slice` در JSON output چیست؟

## پیشرفته
1. در چه شرایطی استفاده از `sync.Pool` منطقی است؟
2. escape analysis چیست و چطور روی GC اثر می‌گذارد؟
3. چگونه memory allocation را در سرویس پرترافیک کاهش می‌دهید؟
4. چه زمانی Generics ارزش افزوده دارد و چه زمانی پیچیدگی اضافه می‌کند؟
5. یک مثال واقعی از bug ناشی از interface design بد بزنید.
