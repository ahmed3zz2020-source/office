# تقني-المكتب — ملاحظات (append-only)
| التاريخ | المعلومة | المصدر |
|---|---|---|
| 2026-10-31 | `memory_read(scope="user")` غير متاح في جلسة تقني-المكتب: tool_search يرجّع 0 نتائج لكل كلمة، mcp_invoke: «Unknown tool_name»، ومفيش أداة memory في catalog الـconnector | probe: tool_search ×6 + mcode-tools connector tools + mcp_invoke |
| 2026-10-31 | قراءة GitHub raw من جوه الساندبوكس شغالة: `curl -s -m 20 -o f -w "RAW:%{http_code}" https://raw.githubusercontent.com/ahmed3zz2020-source/office/main/CHARTER.md` ⇒ RAW:200 وحجم 3326 بايت | curl probe 2026-10-31 |
| 2026-10-31 | سطر الذاكرة (PROTOCOL step 3) اتعذّر — مفيش memory_write برضو | probe 2026-10-31 |
