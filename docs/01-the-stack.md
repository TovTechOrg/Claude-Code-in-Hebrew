<div dir="rtl">

<p align="center"><a href="../README.md">📚 תוכן העניינים</a> &nbsp;|&nbsp; <a href="02-claude-md.md">הבא ←</a></p>

# 🗺️ מפת העולם של Claude – מקצה לקצה

<p align="center"><sub>פרק 1 מתוך 8 · Claude Code בעברית · מעודכן לאוקטובר 2026</sub></p>


רוב מה שעושה את Claude טוב **הוא לא ה־prompt**. זה ההקשר שהוא מקבל, הכלים שמחוברים אליו, וההרשאות שמגדירות מה מותר לו לעשות. לפני שנכנסים ל־Claude Code עצמו, כדאי להבין איפה הוא יושב בתוך המשפחה.

## חמשת "המשטחים" (Surfaces)

| משטח | בשביל מה | דוגמאות |
|------|-----------|----------|
| **claude.ai** | חשיבה, מחקר, תשובות, מסמכים | ניתוח מסמך, טיוטת הצעה, שאלה מורכבת |
| **Claude Cowork** | שכבת התפעול – משימות מתוזמנות ופעולות בין כלים | תדריך בוקר יומי, טיוטות מייל, עדכון Notion/Slack |
| **Claude Design** | תוצרים ויזואליים ומיתוגיים | מוקאפים, דפי נחיתה, פוסטרים, מצגות |
| **Claude Code** | סוכן פיתוח שעובד בתוך תיקייה עם כלים קבועים | כתיבת קוד, תיקון באגים, PR, אוטומציה |
| **Developer Platform** | הטמעת Claude במוצר שלכם | API, Agent SDK, Managed Agents |

> [!NOTE]
> ככל שזזים ימינה בטבלה – משלמים יותר בהקמה, אבל העבודה ממשיכה להתקיים גם בלעדיכם.

## השכבות שמתחת

לכל משטח יש את אותן שכבות יסוד (בדרגות שונות):

- **הקשר (Context)** – `CLAUDE.md`, זיכרון, חוקים (rules)
- **הרחבה (Extend)** – Skills, פקודות (commands), שרתי MCP, Plugins
- **שליטה (Control)** – הרשאות, Plan mode, Hooks
- **סקייל (Scale)** – Subagents, Agent Teams, Workflows
- **אוטומציה (Automate)** – Routines, תזמונים, טריגרים
- **שילוח (Ship)** – אינטגרציה עם GitHub, Vercel וכו'

## איך בוחרים משטח? עץ החלטה מהיר

| אם... | ← עבדו ב |
|-------|-----------|
| צריך לשנות קבצים / קוד | **Claude Code** |
| צריך לרוץ לבד, בלי השגחה | **Cowork** (או **Routine** אם התוצר הוא PR) |
| התוצר ויזואלי | **Claude Design** |
| המשתמשים הם לקוחות של המוצר שלכם | **Developer Platform** |
| כל השאר | **claude.ai** |

## הכלל החשוב: Skills מול Connectors

יש כאן אסימטריה שמבלבלת הרבה אנשים:

- &rlm;**Skills הם פר־משטח.** Claude Code קורא Skills מהדיסק (`.claude/skills/`, `~/.claude/skills/`). Cowork קורא Skills שמוגדרים בחשבון. Skill שכתבתם ב־Claude Code לא יופיע אוטומטית ב־Cowork.
- &rlm;**Connectors (מחברים) הם ברמת החשבון.** מחבר שאישרתם ב־claude.ai (Gmail, Notion, Drive…) זמין לכם בכל המשטחים – כולל Claude Code.

## חדש בסתיו 2026: המשטחים מתחברים

- &rlm;**`/desktop`** (קיצור: `/app`) – ממשיך את הסשן הנוכחי באפליקציית Claude Code Desktop.
- &rlm;**`/teleport`** – מושך סשן ענן אל הטרמינל.
- &rlm;**`/remote-control`** – מאפשר לשלוט בסשן מקומי מתוך claude.ai.
- &rlm;**Artifacts** – Claude Code יכול לפרסם דפי HTML פרטיים ב־claude.ai (`/artifacts` לרשימה), ו־`/design` ו־`/slides` יוצרים עיצובים ומצגות ישירות מהטרמינל.
- &rlm;**Claude Tag** – Claude בתוך Slack (`/install-slack-app`).

---

<p align="center"><a href="../README.md">📚 תוכן העניינים</a> &nbsp;|&nbsp; <a href="02-claude-md.md">הבא: CLAUDE.md ←</a></p>

</div>
