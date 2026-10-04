# 08 · מה חדש – אוגוסט עד אוקטובר 2026

> [← הקודם: מודלים ועלויות](07-models-cost.md) · [תוכן העניינים](../README.md)

סיכום השינויים החשובים בגרסאות **2.1.26x – 2.1.289** (נכון ל־3 באוקטובר 2026). לרשימה המלאה: `/release-notes` בתוך Claude Code, או [ה־changelog הרשמי](https://code.claude.com/docs/en/changelog).

## 🧠 מודלים

| מה | גרסה | פרטים |
|----|-------|--------|
| **Opus 5.5** ברירת מחדל | 2.1.280 | הקשר 1M, פלט עד 128K, $4/$20 – זול מ־Opus 5 |
| **Sonnet 5.5** ברירת מחדל | 2.1.284 | הקשר 1M, $2/$10, קריאת cache $0.20 |
| `fable` עוקב אוטומטית | 2.1.287 | כמו `opus` ו־`sonnet` – תמיד הגרסה האחרונה |
| הקשר 1M כברירת מחדל גם ב־Bedrock/Vertex/Foundry | 2.1.28x | `CLAUDE_CODE_DISABLE_1M_CONTEXT=1` מחזיר ל־200K |

## 🔐 הרשאות

- **Auto mode הוא ברירת המחדל** (2.1.283) בטרמינל וב־VS Code כשלא הוגדר מצב – בכל תוכנית וספק. `permissions.defaultMode` עדיין גובר.
- תשובה חדשה **"Yes, but ask again next time"** לקריאת קבצים מחוץ לתיקיית העבודה (2.1.288).
- כשכמה בקשות הרשאה מצטברות – מונה **"2 of 5"**, והישנה ביותר מוצגת קודם.
- כשהמסווג של auto mode חוסם – הסיבה בדרך כלל **מציינת את הכלל** שהופעל (למשל `[Data Exfiltration]`).
- `rm` על `/` או על תיקיית הבית בתוך `bash -c` מבקש אישור גם ב־`bypassPermissions`.

## 🧩 Plugins, Mods ו־Skills

- **Claude Mods** (2.1.287) – Plugins עם hooks עמוקים וממשק חי (לוחות, פס סטטוס, התראות). Mod מובן: **"You should know"** – סוכן צד שמסמן מה מפספסים.
- **`claude plugin eval`** (2.1.269) – בדיקת Plugin מול מקרי בדיקה, עם ובלי ה־plugin, ודו"ח HTML.
- **`/plugin configure`** (2.1.285) – הגדרת אפשרויות plugin; `--json` לפקודות install/uninstall/update.
- **`/doctor prompt-audit`** (2.1.283) – בודק CLAUDE.md, Skills ו־Agents לדפוסי prompting מיושנים.
- הקלדת `/` באמצע prompt פותחת **רשימת פקודות תואמות**.

## 🤖 סוכנים ו־Workflows

- **Ultracode** הופרד מסליידר ה־effort (2.1.284) – מתג עצמאי בכל רמת effort.
- **הודעות בין סשנים** – Claude מעביר ממצאים בין סשנים במקום העתקה ידנית (`/list-agents`).
- הוסרה מגבלת השעה על פקודות רקע שמפעילים Subagents.
- Workflows שנתקלים במגבלת שימוש **ממתינים לאיפוס** וממשיכים לבד.
- ב־VS Code: **מפת סוכנים** – לחיצה על מונה הסוכנים פותחת transcript לקריאה של כל Subagent.

## 💰 עלויות ו־Cache

- **מד Cache** (אוגוסט) + **סיבה משוערת לכל פספוס** (ספטמבר).
- `/rate-limit-options` (2.1.284) – מה לעשות כשנתקעים במגבלה.
- `/usage` מציג סכומים בדולרים כשיש מגבלת הוצאה ארגונית.
- `maxEffortLevel` – תקרת effort ברמת הארגון או לכל מודל.

## 🖥️ ממשקים

- **`/desktop`** (2.1.285) – פותח את הסשן ב־Claude Code Desktop.
- ב־Desktop: **הוצאת חלוניות** (diff, טרמינל) לחלון נפרד / מסך שני.
- **VS Code:** סימניות (Bookmarks), תצוגה מקדימה לאפשרויות בשאלות, חותמות זמן, כלי Diagnostics שקורא את חלון Problems, "Run in background".
- `/config`, `/mcp`, `/tasks`, `/hooks` – ניווט משופר, עכבר, דפדוף.
- `maxProseWidth` – הגבלת רוחב טקסט בטרמינלים רחבים (קוד וטבלאות נשארים ברוחב מלא).
- **Ctrl+C** מנקה את ה־prompt, ו־**↑** משחזר אותו כולל טקסט מודבק ותמונות.

## 🔌 MCP

- `/mcp reconnect all` – ניסיון חוזר לכל השרתים בבת אחת.
- תמיכה בבקשות URL (התחברות) מהשרת לפי פרוטוקול 2025-11-25.
- `MCP_DISCOVERY_CACHE=1` – שמירת רשימות כלים בין הפעלות (בענן).

## 🏢 לארגונים

- `allowedProviders`, `deniedModels`, `availableModelsMatch: "exact"` – שליטה מדויקת במודלים וספקים.
- `CLAUDE_CODE_DISABLE_WEB_FETCH` – כיבוי WebFetch.
- Claude Tag (Slack): הודעות ישירות, הגבלת ערוצי חיפוש, בחירת "Opus (latest)".

## ❌ הוסר / שונה שם

- `claude project purge` → **`claude purge`**.
- `/ultraplan` הוסר – השתמשו ב־Plan mode.
- `/agents` כבר לא פותח ממשק אינטראקטיבי – בקשו מ־Claude או ערכו את `.claude/agents/`.

---

> [← הקודם: מודלים ועלויות](07-models-cost.md) · [תוכן העניינים](../README.md)
