<div dir="rtl">

<p align="center"><a href="04-reusable-layer.md">→ הקודם</a> &nbsp;|&nbsp; <a href="../README.md">📚 תוכן העניינים</a> &nbsp;|&nbsp; <a href="06-agents-automation.md">הבא ←</a></p>

# ⚡ דף עזר ל־Claude Code

<p align="center"><sub>פרק 5 מתוך 8 · Claude Code בעברית · מעודכן לאוקטובר 2026</sub></p>


מעודכן לגרסה **2.1.289** (3 באוקטובר 2026). הקלידו `/` בתוך סשן כדי לראות את הרשימה המלאה שזמינה לכם.

## התקנה והפעלה

<div dir="ltr">

```bash
# macOS / Linux / WSL
curl -fsSL https://claude.ai/install.sh | bash

# Windows (PowerShell)
irm https://claude.ai/install.ps1 | iex


cd my-project
claude                     # סשן אינטראקטיבי
claude -p "explain this repo" # מצב לא־אינטראקטיבי, לסקריפטים
claude --continue          # המשך הסשן האחרון
```

</div>

חלופות: `brew install --cask claude-code` · `winget install Anthropic.ClaudeCode`. בדיקה: `claude --version` · `claude doctor`.

גם זמין כ־**אפליקציית Desktop** (Mac/Windows), **ב־VS Code ו־JetBrains**, וב־**ווב** (claude.ai/code).

## פקודות – שליטה בסשן

| פקודה | מה היא עושה |
|-------|--------------|
| `/context` | מה תופס את חלון ההקשר עכשיו |
| `/compact [הנחיות]` | סיכום ההיסטוריה, ממשיכים באותה משימה |
| `/clear` | שיחה חדשה ונקייה |
| `/rewind` (`/undo`) | חזרה לנקודה קודמת בשיחה ו/או בקוד |
| `/branch` | פיצול השיחה לכיוון חלופי |
| `/resume` | חזרה לסשן קודם |
| `/recap` | סיכום של שורה אחת של הסשן |
| `/model` | החלפת מודל (חיצים ←/→ לשינוי effort) |
| `/effort [low…max\|auto\|ultracode]` | עומק החשיבה. `ultracode` הוא עכשיו מתג נפרד (2.1.284) |
| `/fast` | מצב מהיר (Opus עם פלט מהיר יותר, לא מודל קטן יותר) |
| `/plan [תיאור]` | כניסה ישירה ל־Plan mode |
| `/goal [תנאי]` | Claude ממשיך לעבוד על פני תורות עד שהתנאי מתקיים |
| `/memory` | עריכת CLAUDE.md וזיכרון אוטומטי |
| `/permissions` | חוקי allow / ask / deny |
| `/usage` (`/cost`, `/stats`) | עלות, מגבלות תוכנית, סטטיסטיקה |
| `/rate-limit-options` | מה לעשות כשנתקעים במגבלת שימוש *(חדש)* |
| `/config` | הגדרות |
| `/diff` | סקירת השינויים בעץ העבודה |
| `/btw [שאלה]` | שאלת צד בלי לזהם את ההקשר |
| `/focus` | תצוגה ממוקדת: רק ה־prompt, סיכום כלים, והתשובה |

## פקודות – השכבה הרב־פעמית וסוכנים

| פקודה | מה היא עושה |
|-------|--------------|
| `/init` | יצירת CLAUDE.md ראשוני (לערוך אחריו!) |
| `/skills` · `/skill-doctor` | רשימת Skills · עלות ושימוש של כל Skill |
| `/mcp` | ניהול שרתי MCP (`reconnect all` חדש) |
| `/plugin` | התקנה/הפעלה של Plugins |
| `/hooks` | צפייה ב־Hooks |
| `/agents` | תזכורת ליצירת Subagents (בקשו מ־Claude או ערכו `.claude/agents/`) |
| `/subtask <משימה>` | Subagent ברקע שיורש את כל השיחה |
| `/fork` · `/background` | העתקת הסשן לרקע · ניתוק הסשן הנוכחי לרקע |
| `/tasks` | עבודה ברקע בסשן |
| `/list-agents` | עם מי Claude יכול לתקשר (Subagents, צוות, סשנים אחרים) |
| `/workflows` | מעקב אחרי Workflows מרובי־סוכנים |
| `/deep-research <שאלה>` | Workflow מובנה למחקר עם מקורות |
| `/code-review` (`/review`) | סקירת diff / PR / branch, עם רמת עומק ו־`--fix` |
| `/security-review` | סקירת אבטחה לשינויים ב־branch |
| `/ultrareview` | סקירה עמוקה מרובת־סוכנים בענן (עולה כסף אמיתי) |
| `/simplify` | ניקוי ופישוט קוד ששונה |
| `/run` · `/verify` | הרצת האפליקציה ובדיקה שהשינוי באמת עובד |
| `/schedule` | יצירת Routines מתוזמנות בענן |
| `/loop [מרווח] [prompt]` | הרצה חוזרת כל עוד הסשן פתוח |
| `/autofix-pr` | סשן ענן שמתקן PR כש־CI נכשל |
| `/doctor [prompt-audit]` | בדיקת התקנה · בדיקת prompts מיושנים *(חדש)* |
| `/insights` | דו"ח HTML על איך אתם משתמשים ב־Claude Code |
| `/desktop` · `/teleport` · `/remote-control` | מעבר בין טרמינל, Desktop וענן |

**הוסרו:** `/ultraplan` (השתמשו ב־Plan mode), `/vim` (דרך `/config`), `/pr-comments` (פשוט בקשו מ־Claude).

## מבנה התיקיות

<div dir="ltr">

```
project-root/
├── CLAUDE.md                ← החוזה, משותף לצוות
├── CLAUDE.local.md          ← אישי, לא נכנס לגיט
├── .mcp.json                ← שרתי הכלים של הצוות
├── docs/                    ← חומר עיון
└── .claude/
    ├── settings.json        ← הרשאות, הוקים ומודל – משותף
    ├── settings.local.json  ← אישי
    ├── rules/               ← חוקים מותנים לפי נתיב
    ├── skills/<name>/SKILL.md
    ├── commands/            ← פקודות סלאש
    └── agents/              ← Subagents

~/.claude/                   ← מקומי למחשב, לא נוסע
├── CLAUDE.md
├── settings.json
├── skills/ · agents/ · commands/
└── projects/<repo>/memory/MEMORY.md
```

</div>

## מצבי הרשאות (Permission Modes)

| מצב | מה רץ בלי לשאול | מתאים ל |
|-----|------------------|---------|
| `default` (**Manual**) | קריאה בלבד | עבודה רגישה, קוד לא מוכר |
| `acceptEdits` | קריאה, עריכות, פקודות קבצים נפוצות | איטרציה על קוד שאתם סוקרים |
| `plan` | קריאה (+פקודות שהמסווג אישר) | חקירה לפני שינוי |
| `auto` | הכל, עם בדיקות בטיחות של מודל־מסווג | משימות ארוכות, פחות "עייפות אישורים" |
| `dontAsk` | רק כלים שאושרו מראש; כל השאר נחסם | CI ותסריטים נעולים |
| `bypassPermissions` | הכל | רק בקונטיינר/VM מבודד! |

- ⭐ **שינוי חשוב (2.1.283):** `auto` הוא **מצב ברירת המחדל** בטרמינל וב־VS Code כשלא הוגדר מצב אחר. `permissions.defaultMode` עדיין גובר.
- &rlm;**`Shift+Tab`** מחליף מצב: auto → manual → acceptEdits → plan → auto.
- חוקי **deny** חוסמים בכל מצב, כולל `bypassPermissions`.
- &rlm;`/auto-mode-setup` מנסח כללי סביבה ל־auto mode מתוך הפרויקט שלכם.
- &rlm;`/sandbox` – ארגז חול ל־Bash (macOS, Linux, WSL2).

## יעילות הקשר

- &rlm;`CLAUDE.md` נטען במלואו בכל סשן → פחות מ־200 שורות.
- זיכרון אוטומטי → רק 200 שורות / 25KB ראשונים.
- &rlm;`@path` בתוך CLAUDE.md → מצמיד קובץ (עד 4 רמות).
- &rlm;`@file` בתוך prompt → מושך את הקובץ לתור אחד.
- &rlm;`.claude/rules/*.md` עם `paths:` → נטען רק בהתאמה.

## קיצורי מקלדת שימושיים

| קיצור | פעולה |
|-------|--------|
| `Shift+Tab` | החלפת מצב הרשאות |
| `Esc` | עצירת Claude באמצע (העבודה שנעשתה נשמרת) |
| `Esc Esc` | עם טקסט: ניקוי הטיוטה · בלי טקסט: תפריט rewind |
| `Ctrl+C` | עצירה, או ניקוי ה־prompt (`↑` משחזר טיוטה כולל תמונות – 2.1.288) |
| `Ctrl+O` | תצוגת transcript מפורטת (כלים, זמנים, מודל) |
| `Ctrl+B` | העברת פקודה/סוכן רץ לרקע |
| `Ctrl+R` | חיפוש בהיסטוריית ה־prompts |
| `Ctrl+T` | הצגה/הסתרה של רשימת המשימות של Claude |
| `Ctrl+G` | עריכת ה־prompt בעורך הטקסט שלכם |
| `Shift+Enter` | שורה חדשה (`/terminal-setup` אם לא עובד) |
| `@` | השלמה אוטומטית של נתיב קובץ |
| `/` באמצע טקסט | רשימת פקודות תואמות |
| `!` בתחילת הודעה | מצב shell – הרצת פקודה ישירות, והפלט נכנס לשיחה |

## עשרה דברים לעשות השבוע

1. להריץ `/context` ולראות מה באמת נטען.
2. לקצץ את CLAUDE.md למה שהקוד לא אומר.
3. להעביר חוקים מותנים ל־`.claude/rules/`.
4. להגדיר הרשאות: קריאה = allow, כתיבה = ask (או לסמוך על auto).
5. להשתמש ב־Plan mode לכל שינוי בכמה קבצים.
6. הוראה שחוזרת על עצמה → Skill.
7. פעולה שחוזרת על עצמה → Command.
8. לחבר מערכת אמיתית אחת דרך MCP.
9. לבקש מ־Claude להסביר קוד שירשתם – הפערים בהסבר = שורות חדשות ל־CLAUDE.md.
10. להריץ `/doctor prompt-audit` אחרי מעבר למודלים 5.5.

---

<p align="center"><a href="04-reusable-layer.md">→ הקודם: השכבה הרב־פעמית</a> &nbsp;|&nbsp; <a href="../README.md">📚 תוכן העניינים</a> &nbsp;|&nbsp; <a href="06-agents-automation.md">הבא: סוכנים ואוטומציה ←</a></p>

</div>
