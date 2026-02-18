<div dir="rtl" align="right">
# Performance + Security Notes (PHP)

## هدف
پاسخ به سوالات حساس عملکرد و امنیت در سیستم‌های واقعی.

## مباحث کلیدی
- performance: cache لایه‌ای، query tuning، queue offloading، profile مداوم.
- امنیت ورودی: validation + sanitization + output escaping.
- auth: session/token lifecycle و revoke strategy.
- OWASP Top 10 را در سطح عملی بشناس (SQLi, XSS, CSRF, SSRF, IDOR).
- rate limiting و brute-force protection ضروری است.
- secret management امن و rotate دوره‌ای.
- audit log برای عملیات حساس (مالی/دسترسی) ضروری است.

## نکات مصاحبه‌ای
- امنیت را به‌عنوان ویژگی معماری بیان کن، نه patch لحظه آخر.
- برای هر ریسک، کنترل پیشگیرانه + کشف + پاسخ تعریف کن.

## تمرین سریع
- یک endpoint حساس را با threat model ساده تحلیل کن.
</div>
