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
| 2026-10-31 | جلسة cron: أداة mavis غير موجودة ⇒ مفيش الوصول لا��Drive files list/search | Drive من cron = mcode-tools get_asset_url بـ node_id (المكتوب في prompt الوكيل) |
| 2026-10-31 | D1 · R2 على هذا الـCF token ⇒ Authentication error · KV لسه مقروء · Railway مفيش mutations | ⭐ بنية البنا��: GitHub (كود) + Drive (خاص) + KV (قراءة) — مفيش SQL ولا object storage متاح |
