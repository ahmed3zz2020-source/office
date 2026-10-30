# سجل الوكلاء

| Agent | Lane | Reads | May write | Cron |
|---|---|---|---|---|
| Mavis (المدير) | توجيه · أولويات · رد نهائي | كل حاجة | الذاكرة (نطاق user) · logs/ | — |
| بوابة-المكتب | استقبال تيليجرام · توزيع | الذاكرة · topics/ | topics/bougate.md · logs/ | كل 5 دقايق |
| مالي-المكتب | الحسابات · الأقساط · التحصيل · المحافظ | PFIS · جدول الأقساط · Drive | topics/finance.md | يومي |
| عقود-المكتب | عقود الشركة · الشقة · DOCX · توقيع | «أساسيات-كتابة-العقود» · topics/contracts.md | topics/contracts.md | عند الطلب |
| تقني-المكتب | OCTA · بوت الذهب · نشر · بنية | الذاكرة (الدروس) · GitHub | topics/tech.md | عند الطلب |
| محتوى-المكتب | cgmz · نصوص · أفكار · نشر | topics/content.md · topics/portfolio.md | topics/content.md | أسبوعي |
| مدقّق-المكتب | مراجعة قبل التسليم | كل المخرَج | topics/lessons.md | قبل كل تسليم |

## قواعد منع الكتابة المتقاطعة
- كل agent يكتب في `topics/<agent>.md` بتاعه بس.
- `logs/YYYY-MM-DD.md` ملف مشترك يومي — كل سطر واحد لكل مهمة، والاسم الأول للوكيل.
- `topics/lessons.md` ⇒ «مدقّق-المكتب» بس (هو اللي بيكتشف الأخطاء المتكررة).
- `AGENTS.md` و`PROTOCOL.md` و`CHARTER.md` ⇒ التعديل它们的 by «المدير» (Mavis) فقط.
