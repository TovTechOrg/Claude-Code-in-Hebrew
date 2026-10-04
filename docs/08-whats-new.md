<div dir="rtl">

<p align="center"><a href="07-models-cost.md">→ הקודם</a> &nbsp;|&nbsp; <a href="../README.md">📚 תוכן העניינים</a></p>

# 🆕 מה חדש – אוגוסט עד אוקטובר 2026

<p align="center"><sub>פרק 8 מתוך 8 · Claude Code בעברית · מעודכן לאוקטובר 2026</sub></p>


סיכום השינויים החשובים בגרסאות **2.1.26x – 2.1.289** (נכון ל־3 באוקטובר 2026). לרשימה המלאה: `/release-notes` בתוך Claude Code, או [ה־changelog הרשמי](https://code.claude.com/docs/en/changelog).

## 🧠 מודלים

| מה | גרסה | פרטים |
|----|-------|--------|
| **Opus 5.5** ברירת מחדל | 2.1.280 | הקשר 1M, פלט עד 128K, $4/$20 – זול מ־Opus 5 |
| **Sonnet 5.5** ברירת מחדל | 2.1.284 | הקשר 1M, $2/$10, קריאת cache $0.20 |
| `fable` עוקב אוטומטית | 2.1.287 | כמו `opus` ו־`sonnet` – תמיד הגרסה האחרונה |
| הקשר 1M כברירת מחדל גם ב־Bedrock/Vertex/Foundry | 2.1.28x | `CLAUDE_CODE_DISABLE_1M_CONTEXT=1` מחזיר ל־200K |

## 🔐 הרשאות

- &rlm;**Auto mode הוא ברירת המחדל** (2.1.283) בטרמינל וב־VS Code כשלא הוגדר מצב – בכל תוכנית וספק. `permissions.defaultMode` עדיין גובר.
- תשובה חדשה **"Yes, but ask again next time"** לקריאת קבצים מחוץ לתיקיית העבודה (2.1.288).
- כשכמה בקשות הרשאה מצטברות – מונה **"2 of 5"**, והישנה ביותר מוצגת קודם.
- כשהמסווג של auto mode חוסם – הסיבה בדרך כלל **מציינת את הכלל** שהופעל (למשל `[Data Exfiltration]`).
- &rlm;`rm` על `/` או על תיקיית הבית בתוך `bash -c` מבקש אישור גם ב־`bypassPermissions`.

## &rlm;🧩 Plugins, Mods ו־Skills

- &rlm;**Claude Mods** (2.1.287) – Plugins עם hooks עמוקים וממשק חי (לוחות, פס סטטוס, התראות). Mod מובן: **"You should know"** – סוכן צד שמסמן מה מפספסים.
- &rlm;**`claude plugin eval`** (2.1.269) – בדיקת Plugin מול מקרי בדיקה, עם ובלי ה־plugin, ודו"ח HTML.
- &rlm;**`/plugin configure`** (2.1.285) – הגדרת אפשרויות plugin; `--json` לפקודות install/uninstall/update.
- &rlm;**`/doctor prompt-audit`** (2.1.283) – בודק CLAUDE.md, Skills ו־Agents לדפוסי prompting מיושנים.
- הקלדת `/` באמצע prompt פותחת **רשימת פקודות תואמות**.

## 🤖 סוכנים ו־Workflows

- &rlm;**Ultracode** הופרד מסליידר ה־effort (2.1.284) – מתג עצמאי בכל רמת effort.
- **הודעות בין סשנים** – Claude מעביר ממצאים בין סשנים במקום העתקה ידנית (`/list-agents`).
- הוסרה מגבלת השעה על פקודות רקע שמפעילים Subagents.
- &rlm;Workflows שנתקלים במגבלת שימוש **ממתינים לאיפוס** וממשיכים לבד.
- ב־VS Code: **מפת סוכנים** – לחיצה על מונה הסוכנים פותחת transcript לקריאה של כל Subagent.

## 💰 עלויות ו־Cache

- **מד Cache** (אוגוסט) + **סיבה משוערת לכל פספוס** (ספטמבר).
- &rlm;`/rate-limit-options` (2.1.284) – מה לעשות כשנתקעים במגבלה.
- &rlm;`/usage` מציג סכומים בדולרים כשיש מגבלת הוצאה ארגונית.
- &rlm;`maxEffortLevel` – תקרת effort ברמת הארגון או לכל מודל.

## 🖥️ ממשקים

- &rlm;**`/desktop`** (2.1.285) – פותח את הסשן ב־Claude Code Desktop.
- ב־Desktop: **הוצאת חלוניות** (diff, טרמינל) לחלון נפרד / מסך שני.
- &rlm;**VS Code:** סימניות (Bookmarks), תצוגה מקדימה לאפשרויות בשאלות, חותמות זמן, כלי Diagnostics שקורא את חלון Problems, "Run in background".
- &rlm;`/config`, `/mcp`, `/tasks`, `/hooks` – ניווט משופר, עכבר, דפדוף.
- &rlm;`maxProseWidth` – הגבלת רוחב טקסט בטרמינלים רחבים (קוד וטבלאות נשארים ברוחב מלא).
- &rlm;**Ctrl+C** מנקה את ה־prompt, ו־**↑** משחזר אותו כולל טקסט מודבק ותמונות.

## &rlm;🔌 MCP

- &rlm;`/mcp reconnect all` – ניסיון חוזר לכל השרתים בבת אחת.
- תמיכה בבקשות URL (התחברות) מהשרת לפי פרוטוקול 2025-11-25.
- &rlm;`MCP_DISCOVERY_CACHE=1` – שמירת רשימות כלים בין הפעלות (בענן).

## 🏢 לארגונים

- &rlm;`allowedProviders`, `deniedModels`, `availableModelsMatch: "exact"` – שליטה מדויקת במודלים וספקים.
- &rlm;`CLAUDE_CODE_DISABLE_WEB_FETCH` – כיבוי WebFetch.
- &rlm;Claude Tag (Slack): הודעות ישירות, הגבלת ערוצי חיפוש, בחירת "Opus (latest)".

## ❌ הוסר / שונה שם

- &rlm;`claude project purge` → **`claude purge`**.
- &rlm;`/ultraplan` הוסר – השתמשו ב־Plan mode.
- &rlm;`/agents` כבר לא פותח ממשק אינטראקטיבי – בקשו מ־Claude או ערכו את `.claude/agents/`.

---

<p align="center"><a href="07-models-cost.md">→ הקודם: מודלים ועלויות</a> &nbsp;|&nbsp; <a href="../README.md">📚 תוכן העניינים</a></p>

</div>
