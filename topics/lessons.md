# دروس المكتب — الأخطاء المتكررة (مدقّق-المكتب فقط)
| التاريخ | الدرس | القاعدة |
|---|---|---|
| 2026-10-31 | Cloudflare KV: سقف الكتابة يومي على مستوى الـaccount كله (429) — صحّة على namespace تاني | probe بـPUT قبل الاعتماد على KV للكتابة؛ السجل في GitHub |
| 2026-10-31 | Workers على workers.dev بترجع 404 | ما نبنيش webhook عليها؛ الاستقبال = polling من cron |
| 2026-10-31 | اسم المدير «Mavis » بمسافة ⇒ cron_create مش بيشتغل عليه | agent بأسم نظيف لكل cron |
| 2026-10-31 | ⛔ ذاكرة الـagents (scope user/agent) معزولة بين الوكلاء — الـcron session بتاع «تقني-المكتب» قرا الذاكرة ف لقى الميثاق مش موجود | ⭐ المصدر المشترك = مستودع GitHub (raw يقرأ بلا توكن · API يكتب بالتوكن) |
| 2026-10-31 | cron_create: مهمة واحدة لكل agent | agent لكل مهمة |
| 2026-10-30 | قراءة بيانات من صورة منخفضة ⇒ تفاصيل مخترعة | crop + قراءة بالعين + مقارنة الرقم القومي |
| 2026-10-31 | جلسة root/cron: `tool_search` يرجّع فاضي ⇒ أدوات on-demand (memory_topic_create · mavis drive) غير موجودة فعليًا | ⭐ مؤشر القدرات = الأدوات المتاحة فعليًا في الجلسة، مش الافتراضية في التعليمات |
| 2026-10-31 | ⛔ raw.githubusercontent بيعمل cache مدته 5 دقايق (x-cache HIT · max-age=300) والـcache-buster ما بيشتغلش ⇒ قراءة logs/topics من raw = قراءة قديمة | ⭐ ملفات متغيرة تُقرأ من GitHub API (Accept: application/vnd.github.raw) — raw بس للملفات النادرة التغير |
| 2026-10-31 | ⛔ Workers على workers.dev بترجع 404 لأن الـsubdomain مش مفعّل — الحل: POST /accounts/<acc>/workers/scripts/<name>/subdomain بـ {"enabled":true,"previews_enabled":true} بعد الـdeploy (النتيجة: 200) | ⭐ الـ404 على workers.dev = subdomain مش مفعّل، مش توكن ناقص |
| 2026-10-31 | ⛔ المستودع office عام ⇒ الرقم القومي والمبالغ كانت مكشوفة في topics/contracts.md و topics/finance.md ⇒ اتشالت | ⭐ grep على أي repo عام قبل push: ارقام 14 رقم · مبالغ · توكنات · بريد |
| 2026-10-31 | جلسة cron: أداة mavis غير موجودة ⇒ مفيش الوصول لاDrive files list/search | Drive من cron = mcode-tools get_asset_url بـ node_id (المكتوب في prompt الوكيل) |
| 2026-10-31 | D1 · R2 على هذا الـCF token ⇒ Authentication error · KV لسه مقروء · Railway مفيش mutations | ⭐ بنية البناء: GitHub (كود) + Drive (خاص) + KV (قراءة) — مفيش SQL ولا object storage متاح |
| 2026-10-31 | ⛔ كل cron بـmode new = session جديد = إعادة حقن system prompt كامل (~24,300 توكن) لتشغيل واحد ⇒ 205 تشغيل/يوم = 5 مليون توكن/يوم | ⭐ cron متكرر ⇒ session mode sessionId · ويومي ⇒ mode new · ومهمة bash واحد ⇒ مش LLM |
| 2026-10-31 | sub-agents: وكيل المكتب (تقني-المكتب) عنده bash + GITHUB_TOKEN + نت · أما General/Coder فمفيش عندهم bash | ⭐ للدراسة المتوازية: task على وكيل المكتب · مش القوالب العامة |
| 2026-10-31 | ⛔ raw.githubusercontent كاش 5 دقايق (max-age=300) والـcache-buster ما بيشتغلش ⇒ logs/topics من raw = قديم | ملفات متغيرة تُقرأ من GitHub API بـAccept: application/vnd.github.raw |
| 2026-10-31 | ⛔ Workers على workers.dev: 404 لأن الـsubdomain مش مفعّل ⇒ الحل POST /workers/scripts/<name>/subdomain بـenabled=true | الـ404 على workers.dev = subdomain مش مفعّل، مش توكن ناقص |
| 2026-10-31 | ⛔ المستودع office عام ⇒ الرقم القومي والمبالغ كانت مكشوفة في topics/contracts.md و topics/finance.md ⇒ اتشالت + فحص آلي | grep على كل repo عام قبل push |
| 2026-10-31 | ⛔ `mode: sessionId` وفّر 54 توكن فقط (0.2%) من 24,480 — لأن أول طلب في كل تشغيل بيتحقن full-price دايماً | ⭐ الحل الحقيقي = تشغيلات أقل + base prompt أصغر · sessionId مش حل اقتصادي |
| 2026-10-31 | قياس: وكيل بـprompt صغير (11,559 input) = نص تكلفة المدير (24,112) | ⭐ أي كرون متكرر ⇒ شغّله على agent صغير مش على «Mavis » |
| 2026-10-31 | ⛔ مهمة bash واحدة (keepalive) كانت بتتنفّذ بنموذج ⇒ 205 تشغيل/يوم × 24,400 توكن | ⭐ قبل أي cron: اكتب «تشغيلات/يوم × توكن/تشغيل» · ومهمة bash = مش LLM |
| 2026-10-31 | 🔴 كل session كرون = **حاوية منفصلة** ⇒ keepalive بيشغّل المحرك من جديد كل مرة ⇒ المحرك عمره ما بيبقى دافي (m15=8 محتاج 40) + 800 KV write/يوم ⇒ السقف خلص | ⭐ أي عملية طويلة العمر لازم تكون في حاوية دايمة، مش في كرون بيشغّلها كل ٧ دقايق |
| 2026-10-31 | ⛔ `mode: sessionId` وفّر 0.2% بس (54 توكن من 24,480) — الاعتماد عليه كحل اقتصادي غلط | القياس قبل الاعتماد · الرافعة الحقيقية = وكيل صغير + جدول أقل |
| 2026-10-31 | ⭐ قرار المالك: بوت الذهب إجازة سبت + صيانة أسبوعية + مراقب كل ساعة —⇒ التكلفة ٢٫٤ مليون ← ٢٧٦ ألف/يوم وKV ٨٠٠+ ← ٨٥/يوم ⇒ المحرك يقدر يدفأ (m15) | ⭐ تقليل تردد الكرون بيصلح سقف KV ⇒ بيصلح دفء المحرك ⇒ بيصلح البوت كله |