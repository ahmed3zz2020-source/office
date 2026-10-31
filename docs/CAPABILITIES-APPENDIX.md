# APPENDIX B — قدرات المنصة وحدودها (متحقق منها بالتجربة 2026-10-31)

المرجع ده اللي بنبني عليه. ⛔ أي سطر مش مكتوب هنا = مش مثبت ⇒ نتأكد قبل ما نعتمد عليه.

## ينفع (متحقق)
| القدرة | الدليل | المصدر |
|---|---|---|
| قراءة مستودع عام بلا توكن | 200 على raw.githubusercontent | اختبار 2026-10-31 |
| قراءة طازجة من GitHub API | SHA بيتغير بعد كل PUT | اختبار 2026-10-31 |
| كتابة على مستودع عام (contents PUT) | 200 على topics/*.md | اختبار 2026-10-31 |
| Worker على workers.dev | 200 بعد تفعيل subdomain | اختبار 2026-10-31 |
| Worker على دومين مخصص | octa-preview + gold-engine | بيئة حية |
| KV قراءة | namespaces gold-signal-bus · gold-signal-bot-state | اختبار 2026-10-31 |
| تيليجرام outbound من cron | gold_scout_xau_bot · chat 2073907990 | 10 مرات متحققة |
| tيليجرام getUpdates (قراءة) | gold bot رجّع ok:true | اختبار 2026-10-31 |
| بحث ويب | search بيرجّع نتائج حقيقية | اختبار 2026-10-31 |
| مولّد صوت عربي | Arabic_CalmWoman · Arabic_FriendlyGuy | اختبار 2026-10-31 |
| بايثون · نود · بلايز رايت · ليبري أوفيس · pdftotext | python3.11 · node · binaries موجودة | اختبار 2026-10-31 |
| نت خارجي من sandbox | 200 على wikipedia | اختبار 2026-10-31 |
| Drive (private) | الملفات بتتسلّم من root session | تجربة سابقة |
| sub-agents داخل الجلسة | task شغّال | اختبار 2026-10-31 |
| cron마다 session فيه كل التوكنات | gold-engine-keepalive شغّال | بيئة حية |

## مش متاح (متحقق)
| الحاجة | السبب | البديل |
|---|---|---|
| مستودع GitHub خاص | التوكن public_repo بس ⇒ 403 | Drive للم secrets · reorganize |
| gists | 404 | — |
| D1 | Authentication error على التوكن | ملفات JSON في GitHub + Drive |
| R2 | Authentication error على التوكن | Drive |
| KV كتابة | سقف يومي 1000 على مستوى الـaccount | GitHub + Drive |
| Railway deploy | التوكن project-scoped بدون mutations | push على main |
| Workers على workers.dev «قبل» تفعيل subdomain | 404 | POST .../subdomain |
| أداة mavis داخل cron session | غير موجودة ⇒ مفيش drive list/search | mcode-tools get_asset_url بـ node_id |
| tool_search داخل sub-agent | الفهرس فاضي ⇒ مفيش bash | sub-agents للقراءة فقط · التنفيذ في root/cron |
| استقبال تيليجرام | البوت الذهبي مشغول على نفس الـoffset | بوت جديد خاص بالمكتب |
| جلسة ثابتة بين الـsub-agents | كل sub-agent سياق مستقل | النتيجة تتكتب في topics/spec.md |

## قواعد الكفاءة (credits)
- sub-agent = سياق مستقل مكلف ⇒ استخدمه للقراءة والتحليل، مش للتنفيذ المتكرر.
- cron = session كل تشغيل ⇒ cron للعامل اليومي بس (صباح · ليل · بوابة).
- study مرة واحدة ⇒ ناتجها في topics/spec.md ⇒ الـSlices تقرأ النتيجة، مش البرومبت تاني.
- ⛔ ما تعملش probe لحديمة مثبتة ⇒ اقرأ topics/lessons.md.

##不清楚 (مش محسومة)
- هل_BINDINGS PUT (405) بيتحل بـmultipart صحيح ولا لأ — محتاجkusمة أول.
- هل مينفع نوصل لحدود 1000 KV write/يوم بعد تخفيف keepalive ولا لأ — محتاج تجربة يوم كامل.
