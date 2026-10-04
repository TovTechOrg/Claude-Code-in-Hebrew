# 01 · מפת העולם של Claude – מקצה לקצה

> [← חזרה לתוכן העניינים](../README.md) · [הבא: CLAUDE.md ←](02-claude-md.md)

רוב מה שעושה את Claude טוב **הוא לא ה־prompt**. זה ההקשר שהוא מקבל, הכלים שמחוברים אליו, וההרשאות שמגדירות מה מותר לו לעשות. לפני שנכנסים ל־Claude Code עצמו, כדאי להבין איפה הוא יושב בתוך המשפחה.

## חמשת "המשטחים" (Surfaces)

| משטח | בשביל מה | דוגמאות |
|------|-----------|----------|
| **claude.ai** | חשיבה, מחקר, תשובות, מסמכים | ניתוח מסמך, טיוטת הצעה, שאלה מורכבת |
| **Claude Cowork** | שכבת התפעול – משימות מתוזמנות ופעולות בין כלים | תדריך בוקר יומי, טיוטות מייל, עדכון Notion/Slack |
| **Claude Design** | תוצרים ויזואליים ומיתוגיים | מוקאפים, דפי נחיתה, פוסטרים, מצגות |
| **Claude Code** | סוכן פיתוח שעובד בתוך תיקייה עם כלים קבועים | כתיבת קוד, תיקון באגים, PR, אוטומציה |
| **Developer Platform** | הטמעת Claude במוצר שלכם | API, Agent SDK, Managed Agents |

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

```
צריך לשנות קבצים / קוד?          ← Claude Code
צריך לרוץ לבד, בלי השגחה?          ← Cowork (או Routine אם התוצר הוא PR)
התוצר ויזואלי?                     ← Claude Design
המשתמשים הם לקוחות של המוצר שלכם? ← Developer Platform
כל השאר                            ← claude.ai
```

## הכלל החשוב: Skills מול Connectors

יש כאן אסימטריה שמבלבלת הרבה אנשים:

- **Skills הם פר־משטח.** Claude Code קורא Skills מהדיסק (`.claude/skills/`, `~/.claude/skills/`). Cowork קורא Skills שמוגדרים בחשבון. Skill שכתבתם ב־Claude Code לא יופיע אוטומטית ב־Cowork.
- **Connectors (מחברים) הם ברמת החשבון.** מחבר שאישרתם ב־claude.ai (Gmail, Notion, Drive…) זמין לכם בכל המשטחים – כולל Claude Code.

## חדש בסתיו 2026: המשטחים מתחברים

- **`/desktop`** (קיצור: `/app`) – ממשיך את הסשן הנוכחי באפליקציית Claude Code Desktop.
- **`/teleport`** – מושך סשן ענן אל הטרמינל.
- **`/remote-control`** – מאפשר לשלוט בסשן מקומי מתוך claude.ai.
- **Artifacts** – Claude Code יכול לפרסם דפי HTML פרטיים ב־claude.ai (`/artifacts` לרשימה), ו־`/design` ו־`/slides` יוצרים עיצובים ומצגות ישירות מהטרמינל.
- **Claude Tag** – Claude בתוך Slack (`/install-slack-app`).

---

> [← חזרה לתוכן העניינים](../README.md) · [הבא: CLAUDE.md ←](02-claude-md.md)
