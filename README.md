<div dir="rtl">

# &rlm;Claude Code בעברית 🇮🇱

**מדריך מעשי ומלא ל־Claude Code – בעברית, מעודכן לאוקטובר 2026 (גרסה 2.1.289).**

🌐 **[לגרסת האתר (GitHub Pages)](https://tovtechorg.github.io/Claude-Code-in-Hebrew/)**

> רוב מה שעושה את Claude טוב **הוא לא ה־prompt** – אלא ההקשר, הכלים וההרשאות. המדריך הזה מסביר איך לבנות אותם נכון.

## 📚 תוכן העניינים

| # | פרק | על מה |
|---|-----|--------|
| 01 | [מפת העולם של Claude](docs/01-the-stack.md) | חמשת המשטחים, השכבות, ואיך בוחרים איפה לעבוד |
| 02 | [CLAUDE.md – החוזה](docs/02-claude-md.md) | מה לכתוב, ארבע הרמות, ייבוא עם `@`, חוקים מותנים |
| 03 | [הקשר וזיכרון](docs/03-context-memory.md) | זיכרון אוטומטי מול זיכרון בריפו, `/context`, `/compact`, אחזור |
| 04 | [השכבה הרב־פעמית](docs/04-reusable-layer.md) | Skills, פקודות, MCP, Plugins ו־Mods |
| 05 | [דף עזר](docs/05-cheat-sheet.md) | התקנה, כל הפקודות החשובות, מבנה תיקיות, מצבי הרשאות, קיצורים |
| 06 | [סוכנים ואוטומציה](docs/06-agents-automation.md) | Subagents, Agent view, Teams, Workflows, Routines, Managed Agents |
| 07 | [מודלים, Effort ועלויות](docs/07-models-cost.md) | Opus 5.5, Sonnet 5.5, Fable 5.1, Haiku 4.5, Caching, מנויים |
| 08 | [מה חדש (אוג׳–אוק׳ 2026)](docs/08-whats-new.md) | כל השינויים החשובים בגרסאות האחרונות |

## 🚀 התחלה מהירה

<div dir="ltr">

```bash
# macOS / Linux / WSL
curl -fsSL https://claude.ai/install.sh | bash

# Windows (PowerShell)
irm https://claude.ai/install.ps1 | iex

cd my-project
claude
```

</div>

ואז, בתוך הסשן:

1. &rlm;`/init` – יוצר `CLAUDE.md` ראשוני. **ערכו אותו** – השאירו רק את מה שהקוד לא אומר.
2. &rlm;`/context` – ראו מה באמת נטען לחלון ההקשר.
3. &rlm;`Shift+Tab` – החליפו בין מצבי הרשאות (ברירת המחדל עכשיו: **auto**).
4. לשינוי בכמה קבצים – התחילו ב־`/plan`.

## ✅ עשרה דברים לעשות השבוע

1. להריץ `/context`.
2. לקצץ את CLAUDE.md לפחות מ־200 שורות.
3. להעביר חוקים מותנים ל־`.claude/rules/` עם `paths:`.
4. להגדיר הרשאות: קריאה = allow, כתיבה = ask.
5. &rlm;Plan mode לכל שינוי רב־קבצים.
6. הוראה שחוזרת → Skill.
7. פעולה שחוזרת → Command.
8. לחבר מערכת אמיתית אחת דרך MCP.
9. לבקש מ־Claude להסביר קוד שירשתם – הפערים = שורות חדשות ל־CLAUDE.md.
10. להריץ `/doctor prompt-audit` אחרי המעבר למודלים 5.5.

## 🗂️ מבנה הריפו

<div dir="ltr">

```
.
├── README.md          ← אתם כאן
├── index.html         ← אתר האינטרנט (עמוד אחד)
└── docs/              ← פרקי המדריך
    ├── 01-the-stack.md
    ├── ...
    └── 08-whats-new.md
```

</div>

### הפעלת GitHub Pages

&rlm;`Settings` → `Pages` → `Source: Deploy from a branch` → `main` / `/ (root)`. האתר יעלה בכתובת `https://<user>.github.io/<repo>/`.

## 📖 מקורות

- [התיעוד הרשמי של Claude Code](https://code.claude.com/docs)
- &rlm;[Changelog רשמי](https://code.claude.com/docs/en/changelog)
- [סקירת המודלים – Claude Platform](https://platform.claude.com/docs/en/models/opus-5-5/overview)
- המבנה הרעיוני מבוסס על [Claude Camp Toolkit](https://claudecamp.ai/toolkit/read) (אוגוסט 2026), מתורגם, מעובד ומעודכן לאוקטובר 2026.

> [!WARNING]
> &rlm;Claude Code מתעדכן כמעט כל יום. אם משהו לא תואם – בדקו `/release-notes` אצלכם ופתחו Issue / PR.

---

<sub>🙏 תודה ל־<a href="https://claudecamp.ai/">Claude Camp</a> על ההשראה והמבנה המקורי.</sub>

</div>
