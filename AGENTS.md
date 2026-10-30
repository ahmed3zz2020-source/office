# سجل الوكلاء

⚠️ **المصدر المشترك الوحيد = هذا المستودع.** ذاكرة كل agent معزولة ⇒ ما تعتمدش عليها للتنسيق.
اقرأ أول كل تشغيل: `CHARTER.md` ثم `PROTOCOL.md` ثم `AGENTS.md` ثم آخر سطرين في `logs/YYYY-MM-DD.md`.
القراءة: `curl https://raw.githubusercontent.com/ahmed3zz2020-source/office/main/<FILE>` (بلا توكن).
الكتابة: GitHub API content PUT (${GITHUB_TOKEN} في البيئة).

| Agent | Lane | Reads | May write | Cron |
|---|---|---|---|---|
| Mavis (المدير) | توجيه · أولويات · رد نهائي | كل حاجة | CHARTER/PROTOCOL/AGENTS + logs/ | — |
| بوابة-المكتب | استقبال تيليجرام · توزيع · رد | CHARTER · AGENTS · logs | topics/gate.md | كل 5 دقايق |
| مالي-المكتب | الحسابات · الأقساط · التحصيل · المحافظ | topics/finance.md · PFIS · drive | topics/finance.md | يومي |
| عقود-المكتب | عقود الشركة · الشقة · DOCX · توقيع | topics/contracts.md · drive | topics/contracts.md | عند الطلب |
| تقني-المكتب | OCTA · بوت الذهب · نشر · بنية | topics/tech.md | topics/tech.md | عند الطلب |
| محتوى-المكتب | cgmz · نصوص · أفكار · نشر | topics/content.md | topics/content.md | أسبوعي |
| مدقّق-المكتب | مراجعة قبل التسليم | كل المخرَج | topics/lessons.md | قبل كل تسليم |

## منع الكتابة المتقاطعة
- كل agent يكتب في `topics/<agent>.md` بتاعه بس.
- `logs/YYYY-MM-DD.md` مشترك · سطر واحد لكل مهمة · اسم الوكيل الأول.
- `topics/lessons.md` ⇒ «مدقّق-المكتب» بس.
- `CHARTER.md` · `PROTOCOL.md` · `AGENTS.md` ⇒ «المدير» (Mavis) فقط.

## حدود معروفة (لا تختبرها كل مرة)
- ⛔ Cloudflare KV: كتابة 429 (سقف يومي account) ⇒ قراءة فقط.
- ⛔ Workers على workers.dev: 404 ⇒ لا webhook.
- ⛔ Railway: لا مشروع جديد (Deploys paused) ⇒ الباك بـpush على main.
- ⛔ GitHub: لا مستودع خاص ⇒ الكود في مستودع عام ⇒ **ما تحطش بيانات شخصية أو أسرار في الكود**.
