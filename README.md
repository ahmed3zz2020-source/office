> ⭐ **تحديث ٣١ أكتوبر ٢٠٢٦:** أُنشئت **مؤسسة EZZ** — انظر `https://github.com/ahmed3zz2020-source/EZZ`.
> هذا المستودع بقى **غرفة العمليات** (OCTA · بوت الذهب · كرونات التشغيل). **عقل المؤسسة** = مستودع EZZ (الدستور · الذاكرة · الوكلاء · القرارات).
> ⛔ ما تحطش بيانات شخصية في أي منهما — المستودعان عامّان.

# مكتب أحمد — Central Office

This repo is the **versioned home** of the office system: charter, protocols, per-agent briefs, and the daily log index.
It is the source of truth for *structure*. Personal/financial data never lands here (repos are public) — that lives in the agent memory (scope=user) and the Drive.

## Point of entry for every agent
1. Read `CHARTER.md` (the rules).
2. Read `PROTOCOL.md` (the 5 steps).
3. Read `AGENTS.md` (your lane + where to write).
4. Read the agent memory `memory_read(scope="user")` — first 120 lines = live charter + latest state.
5. Then work.

## Layout
```
CHARTER.md      the office charter (rules, boundaries, language rules)
PROTOCOL.md     5-step operating protocol + failure handling
AGENTS.md       roster: agent → lane → cron → what it may write
topics/         one file per agent: its own notes (append-only)
logs/           daily log index (one line per task)
templates/      report templates (morning brief, night report, task log)
```

## Hard rules (never break)
- Never invent data. A number without a source = "no data".
- Never publish to octashares.com without Ahmed saying "ارفع على الدومين". Preview is the default.
- Never name any AI tool in any output.
- No boxes, no arrows. Each item on its own line. English words inside Arabic sentences go in parentheses.
- Arabic replies, Egyptian dialect, short, readable on a phone.
