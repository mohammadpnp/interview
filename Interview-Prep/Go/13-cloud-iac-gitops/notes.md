<div dir="rtl" align="right">
# Cloud + IaC + GitOps Notes (Go)

## هدف
آمادگی برای سوالات Cloud/Infra که در نقش‌های Senior Backend زیاد پرسیده می‌شود.

## مباحث کلیدی
- IaC با Terraform/Ansible خطای دستی را کم و reproducibility را زیاد می‌کند.
- Helm برای مدیریت نسخه deployment در Kubernetes کاربردی است.
- GitOps یعنی desired state در git و reconcile خودکار در کلاستر.
- محیط‌های cloud/hybrid نیازمند observability و policy یکپارچه‌اند.
- storage/networking در cloud باید با SLA سرویس هم‌راستا طراحی شود.
- secrets management و least-privilege برای امنیت عملیاتی مهم است.
- rollout، rollback، و disaster recovery باید مستند و تمرین‌شده باشند.

## نکات مصاحبه‌ای
- صرف نام ابزار کافی نیست؛ workflow واقعی apply/review/rollback را توضیح بده.
- از زاویه reliability + cost هم تحلیل کن.

## تمرین سریع
- یک سرویس Go را با Helm deploy کن و تغییر config را به‌صورت GitOps مدیریت کن.
</div>
