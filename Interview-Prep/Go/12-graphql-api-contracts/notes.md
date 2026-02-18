# GraphQL + API Contracts Notes (Go)

## هدف
پوشش سوالات GraphQL و قرارداد API که کنار REST/gRPC در بازار مطرح است.

## مباحث کلیدی
- GraphQL برای aggregation و نیاز متنوع کلاینت‌ها مناسب است.
- مشکل N+1 در GraphQL رایج است؛ DataLoader و batching حیاتی‌اند.
- schema design باید domain-aware و version-aware باشد.
- authorization باید field-level و resolver-level بررسی شود.
- complexity/depth limit برای جلوگیری از queryهای مخرب لازم است.
- برای API contract، OpenAPI/Proto/GraphQL schema باید source of truth باشد.
- breaking change policy و deprecation window باید تعریف شود.

## نکات مصاحبه‌ای
- GraphQL را جایگزین کامل REST معرفی نکن؛ hybrid approach را توضیح بده.
- امنیت و performance را هم‌زمان در طراحی resolverها پوشش بده.

## تمرین سریع
- یک schema برای Order + User بنویس و N+1 را با DataLoader کنترل کن.
