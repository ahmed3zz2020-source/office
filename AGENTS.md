# سجل الوكلاء

المصدر المشترك = هذا المستودع. ذاكرة كل agent معزولة ⇒ ما تعتمدش عليها للتنسيق.
اقرأ اول كل تشغيل: CHARTER.md ثم PROTOCOL.md ثم AGENTS.md ثم آخر سطرين في logs/<اليوم>.md.

## طريقة القراءة (مهمة)
- نادر التغير (CHARTER · PROTOCOL · AGENTS · templates): raw.githubusercontent بلا توكن.
- متغير (logs · topics): GitHub API مع Accept: application/vnd.github.raw و ${GITHUB_TOKEN}.
السبب: raw بيعمل cache 5 دقايق ⇒ قراءة قديمة ⇒ قرار غلط.

## طريقة الكتابة
GitHub API contents PUT بـ ${GITHUB_TOKEN}.
⛔ ما تكتبش بيانات شخصية او ارقام قومية او مبالغ — المستودع عام.

| Agent | Lane | Reads | May write | Cron |
|---|---|---|---|---|
| Mavis (المدير) | توجيه · اولويات · رد نهائي | كل حاجة | CHARTER/PROTOCOL/AGENTS + logs + topics/spec.md | — |
| بوابة-المكتب | استقبال تيليجرام · توزيع · رد | CHARTER · AGENTS · logs | topics/gate.md | كل 5 دقايق (متوقف لحد توكن) |
| مالي-المكتب | الحسابات · الاقساط · التحصيل · المحافظ | topics/finance.md · Drive خاص | topics/finance.md | يومي |
| عقود-المكتب | عقود الشركة · الشقة · DOCX · توقيع | topics/contracts.md · Drive خاص | topics/contracts.md | عند الطلب |
| تقني-المكتب | OCTA · بوت الذهب · نشر · بنية | topics/tech.md | topics/tech.md | عند الطلب |
| محتوى-المكتب | cgmz · نصوص · افكار · نشر | topics/content.md | topics/content.md | اسبوعي |
| مدقق-المكتب | مراجعة قبل التسليم | كل المخرج | topics/lessons.md | قبل كل تسليم |
| مكتب-الصباح | تنفيذ تقرير الصباح | CHARTER · logs · topics/* | logs + ملف المخرج | 07:00 القاهرة |
| مكتب-الليل | تنفيذ تقرير الليل | CHARTER · logs · lessons | logs + ملف المخرج | 22:30 القاهرة |

## منع الكتابة المتقاطعة
- كل agent يكتب في topics/<agent>.md بتاعه بس.
- logs/YYYY-MM-DD.md مشترك · سطر واحد لكل مهمة · اسم الوكيل الاول.
- topics/lessons.md = مدقق-المكتب بس.
- topics/spec.md = المدير بس (مواصفات المشروع الكبير).
- CHARTER.md · PROTOCOL.md · AGENTS.md = المدير بس.

## ملفات جديدة (2026-10-31)
- templates/big-spec-protocol.md = بروتوكول استقبال البرومبت الكبير (دراسة قبل بناء).
- templates/requirements-spec.md = قالب المواصفات المرقّمة.
- templates/phase-plan.md = قالب خطة المراحل (قطع قابلة للتسليم).
- topics/spec.md = مساحة عمل المواصفات (-REQ-).

## حدود معروفة (لا تختبرها كل مرة)
- Cloudflare KV: كتابة 429 (سقف يومي account) ⇒ قراءة فقط.
- Workers: شغال على workers.dev بعد تفعيل subdomain (POST .../subdomain).
- D1 · R2: Authentication error على هذا التوكن ⇒ غير متاح.
- Railway: مفيش deploy (توكن project-scoped بدون mutations).
- GitHub: مفيش مستودع خاص ⇒ الكود عام ⇒ ⛔ ما تحطش بيانات شخصية.
- cron: مهمة واحدة لكل agent · session فيه كل التوكنات · مفيش أداة mavis ⇒ Drive بـ get_asset_url.
