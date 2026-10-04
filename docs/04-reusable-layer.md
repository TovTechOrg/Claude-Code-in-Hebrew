<div dir="rtl">

<p align="center"><a href="03-context-memory.md">→ הקודם</a> &nbsp;|&nbsp; <a href="../README.md">📚 תוכן העניינים</a> &nbsp;|&nbsp; <a href="05-cheat-sheet.md">הבא ←</a></p>

# 🧩 השכבה הרב־פעמית: Skills, פקודות, MCP, Plugins ו־Mods

<p align="center"><sub>פרק 4 מתוך 8 · Claude Code בעברית · מעודכן לאוקטובר 2026</sub></p>


## חמש אבני הבניין

| אבן בניין | מה זה | איפה |
|-----------|--------|-------|
| **Skill** | מתכון/התנהגות – "איך עושים X" | `.claude/skills/<name>/SKILL.md` |
| **Command** | פעולת `/slash` שמפעילים לפי דרישה | `.claude/commands/<name>.md` |
| **MCP** | חיבור לכלים ומערכות חיצוניות | `.mcp.json` או Connector בחשבון |
| **Plugin** | חבילה של כל הנ"ל (+ Agents, Hooks) | `/plugin install` |
| **Mod** *(חדש, 2.1.287)* | Plugin עם hooks עמוקים וממשק חי בתוך Claude Code | `/plugin-authoring` |

## מה הולך לאן? עץ החלטה

| מה זה? | ← איפה לשים |
|--------|--------------|
| עובדה על הפרויקט | `CLAUDE.md` |
| איך עושים משהו | Skill |
| משימה שמפעילים ביד | Command (או Skill עם `/שם`) |
| גישה למערכת אחרת | MCP / Connector |
| חומר עיון | `docs/` |
| הרשאות, מודל, Hooks | `.claude/settings.json` |

### מטריצת רלוונטיות

| כמה רלוונטי? | איפה לשים | איך נטען |
|---------------|-----------|-----------|
| תמיד | `CLAUDE.md` | כל סשן, במלואו |
| רק לחלק מהקבצים | `.claude/rules/*.md` עם `paths:` | רק כשנוגעים בקבצים תואמים |
| מדי פעם | `docs/` | כשקוראים או מזכירים עם `@` |

## &rlm;Skills

<div dir="ltr">

```markdown
---
name: release-notes
description: כתיבת הערות גרסה מהיסטוריית הגיט. השתמש כשמבקשים "מה השתנה".
---
1. הרץ `git log --oneline <tag>..HEAD`.
2. קבץ לפי feat / fix / chore.
3. ...
```

</div>

- רק ה־`description` נטען תמיד; הגוף נטען כשה־Skill מופעל. לכן התיאור צריך לומר **מתי** להשתמש.
- **כתבו Skill אחרי שעשיתם משהו פעמיים**, לא לפני.
- &rlm;`.claude/commands/x.md` ו־`.claude/skills/x/SKILL.md` – שניהם נותנים `/x`.
- אפשר לשרשר עד 6 Skills: `/skill-a /skill-b עשה XYZ`.
- &rlm;`/reload-skills` טוען Skills חדשים בלי להפעיל מחדש.
- &rlm;Skills מובנים שימושיים: `/code-review`, `/simplify`, `/run`, `/verify`, `/batch`, `/loop`, `/debug`, `/fewer-permission-prompts`, `/update-config`.

## &rlm;MCP – Model Context Protocol

מחבר את Claude למערכות חיצוניות (Postgres, Stripe, Notion, GitHub, Sentry…). שאלה אחת → כמה קריאות כלים במקביל → תשובה מאוחדת. בלי אינטגרציה ייעודית.

**שתי דרכים להפעיל:**
1. &rlm;**Connectors בחשבון** – OAuth דרך claude.ai, עוברים איתכם לכל משטח.
2. **שרתים מקובץ** – `.mcp.json` בשורש הריפו (משותף לצוות) או `~/.claude.json` (אישי).

<div dir="ltr">

```json
{
  "mcpServers": {
    "postgres": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-postgres", "postgresql://localhost/dev"]
    }
  }
}
```

</div>

**הרשאות:** כלי קריאה → always-allow. כלי כתיבה → להשאיר על ask.

**חדש בספטמבר–אוקטובר 2026:**
- &rlm;`/mcp reconnect all` – מנסה מחדש את כל השרתים שנכשלו או דורשים התחברות.
- &rlm;`/mcp` מציג יותר כלים, עם גלילה ועכבר, ומסמן כלים שהארגון חסם.
- תמיכה בבקשות URL מהשרת (התחברות) לפי פרוטוקול MCP 2025-11-25.

## &rlm;Plugins

<div dir="ltr">

```
/plugin marketplace add <owner/repo>
/plugin install <name>@<marketplace>
/plugin configure <name>          ← חדש: הגדרת אפשרויות
/reload-plugins                   ← טעינה מחדש בלי הפעלה מחדש
```

</div>

> [!WARNING]
> **קראו מה שאתם מתקינים.** Plugin יכול להכיל הוראות שמשנות את התנהגות Claude בכל מקום, Hooks שמריצים קוד, ושרתי MCP.

### בדיקת Plugins – `claude plugin eval` (חדש, 2.1.269)

```bash
claude plugin eval init   # שואל מה זו תוצאה טובה ומציע מקרי בדיקה
claude plugin eval .      # מריץ ונותן ציון, עם ובלי התוסף
```

הדו"ח המלא נשמר ב־`evals/results/report.html`. כל ריצה היא קריאת מודל אמיתית בחשבון שלכם.

## &rlm;Mods (חדש, 2.1.287)

&rlm;Mods הם Plugins שיכולים להתחבר עמוק יותר: לוחות חיים, פס סטטוס, התראות, hooks כפונקציות – עם hot-reload בתוך הסשן.

- דוגמה מובנית: **"You should know"** – סוכן צד שעוקב ומסמן דברים שאתם או Claude עלולים לפספס:
  `/plugin enable cc-plugin-you-should-know@builtin`
- לכתוב Mod משלכם: בקשו מ־Claude, או `/plugin-authoring`.

---

<p align="center"><a href="03-context-memory.md">→ הקודם: הקשר וזיכרון</a> &nbsp;|&nbsp; <a href="../README.md">📚 תוכן העניינים</a> &nbsp;|&nbsp; <a href="05-cheat-sheet.md">הבא: דף עזר ←</a></p>

</div>
