# APPENDIX B — قدرات المنصة وحدودها (متحقق منها بالتجربة 2026-10-31)

المرجع ده اللي بنبني عليه. ⛔ أي سطر مش مكتوب هنا = مش مثبت ⇒ نتأكد قبل ما نعتمد عليه.

## ينفع (متحقق)
| القدرة | الدليل |
|---|---|
| قراءة مستودع عام بلا توكن | 200 على raw.githubusercontent |
| قراءة طازجة من GitHub API | SHA بيتغير بعد كل PUT · Accept: application/vnd.github.raw |
| كتابة على مستودع عام (contents PUT) | 200 على topics/*.md |
| Worker على workers.dev | 200 بعد POST /workers/scripts/<name>/subdomain بـ enabled=true |
| Worker بــKV binding | Upload multipart بـtype=module + Content-Type application/javascript+module ⇒ 200 · لكن الطلب رجّع 1101 (الـbinding اتربط بعد multipart بـmetadata ⇒ محتاج إعادة اختبار) |
| KV قراءة + كتابة | namespaces gold-signal-bus · gold-signal-bot-state — كتابة رجعت success:true |
| تيليجرام outbound من cron | gold_scout_xau_bot · chat 2073907990 · 10 مرات متحققة |
| تيليجرام getUpdates (قراءة) | gold bot رجّع ok:true |
| بحث ويب | search بيرجّع نتائج حقيقية |
| مولد صوت عربي | Arabic_CalmWoman · Arabic_FriendlyGuy |
| بايثون 3.11 · نود · بلايز رايت · ليبري أوفيس · pdftotext | binaries موجودة |
| نت خارجي من sandbox | 200 على wikipedia |
| Drive (خاص) | الملفات بتتسلّم من root session |
| sub-agent من وكيل المكتب (task) | عنده bash كامل + GITHUB_TOKEN + نت ⇒ يقدر يقرأ ويكتب المستودع |
| sub-agent من General/Coder | ⛔ مفيش bash ⇒ للفكرة والتلخيص فقط |
| cron session فيه كل التوكنات | gold-engine-keepalive شغال |
| cron_update بـsession.session_id حقيقي | اشتغل (keepalive بقى sessionId) |
| cron_update بـsession.session_id = fixed | ⛔ مرفوض (fixed للخلق بس) |

## مش متاح (متحقق)
| الحاجة | السبب | البديل |
|---|---|---|
| مستودع GitHub خاص | التوكن public_repo بس ⇒ 403 | Drive للخاص |
| gists | 404 | — |
| D1 | Authentication error | ملفات JSON في GitHub + Drive |
| R2 | Authentication error | Drive |
| KV كتابة量大 | سقف يومي 1000 على مستوى الـaccount | GitHub + Drive + تقليل الكتابة |
| Railway deploy | التوكن project-scoped بدون mutations | push على main |
| cron daemon جوّه الـcontainer | ⛔ مفيش binary ولا busybox ⇒ cron نظامي غير متاح | cron المنصة أو background loop |
| أداة mavis داخل cron session | غير موجودة ⇒ مفيش drive list/search | mcode-tools get_asset_url بـ node_id |
| tool_search داخل sub-agent عام | الفهرس فاضي ⇒ مفيش bash | استخدم وكيل المكتب كـsub-agent |
| استقبال تيليجرام | البوت الذهبي مشغول على نفس الـoffset | بوت جديد خاص بالمكتب |
| جلسة ثابتة بين الـsub-agents | كل sub-agent سياق مستقل | النتيجة تتكتب في topics/spec.md |

## كفاءة الكريدت — الأرقام المقيسة
| البند | الرقم |
|---|---|
| تشغيل واحد cron mode new | 24,534 توكن (input 24,112 + output 138 + cache_read 284) |
| المخرج المفيد من التشغيل ده | 5 توكن («engine ok») |
| gold-engine-keepalive (*/7) | 205 تشغيل/يوم ≈ 5 مليون توكن/يوم |
| بوابة الاستقبال (*/5) | 288 تشغيل/يوم ≈ 7 مليون توكن/يوم (اتوقفت) |
| session_messages بـ5 رسائل | 42,379 توكن |
| agent list بـ20 agent | ≈ 12,300 توكن |
