<div dir="rtl">

<p align="center"><a href="01-the-stack.md">→ הקודם</a> &nbsp;|&nbsp; <a href="../README.md">📚 תוכן העניינים</a> &nbsp;|&nbsp; <a href="03-context-memory.md">הבא ←</a></p>

# &rlm;📜 CLAUDE.md – החוזה בינכם לבין Claude

<p align="center"><sub>פרק 2 מתוך 8 · Claude Code בעברית · מעודכן לאוקטובר 2026</sub></p>


&rlm;`CLAUDE.md` הוא קובץ Markdown שנטען **בתחילת כל סשן**. הוא החוזה: מה Claude חייב לדעת על הפרויקט כדי לא לטעות.

## העיקרון המרכזי

כתבו ב־CLAUDE.md **את מה שהקוד לא אומר**. לא תיאור של התיקיות, לא רשימת התלויות – את זה Claude רואה בעצמו.

המבחן לכל שורה: **האם Claude היה טועה בלעדיה?** אם לא – מחקו אותה. כל שורה עולה טוקנים בכל תור.

## ארבע רמות (מצטרפות, לא דורסות)

| רמה | מיקום | מי רואה |
|-----|-------|----------|
| **Managed** | מדיניות ארגונית (מנוהלת ע"י IT) | כל הארגון |
| **User** | `~/.claude/CLAUDE.md` | רק אתם, בכל הפרויקטים, רק במחשב הזה |
| **Project** | `./CLAUDE.md` או `./.claude/CLAUDE.md` | כל הצוות (נכנס ל־git) |
| **Local** | `./CLAUDE.local.md` | רק אתם, בפרויקט הזה (ב־gitignore) |

כל הרמות **מחוברות יחד** ל־prompt אחד. Claude עולה במעלה עץ התיקיות וטוען כל `CLAUDE.md` שהוא מוצא; קבצים בתתי־תיקיות נטענים רק כשעובדים עליהן.

## מבנה מומלץ (פחות מ־200 שורות)

```markdown
# שם הפרויקט
משפט-שניים: מה זה ולמי.

## Stack
רק החלקים הלא-צפויים (למשל: "Postgres 17 עם RLS, לא Prisma").

## קונבנציות
מה שהייתם מעירים עליו ב-Code Review.

## תמיד
- להריץ `pnpm test` לפני שמסיימים.
- ...

## לעולם לא
- לא לגעת ב-`migrations/` ידנית.
- ...   ← הסעיף הכי שווה. נולד מכשלונות אמיתיים.

## מוקשים (Gotchas)
- `config.ts` נטען פעמיים ב-dev – זה מכוון.
```

## ייבוא קבצים עם `@`

<div dir="ltr">

```markdown
@docs/architecture.md
@~/.claude/my-preferences.md
```

</div>

- &rlm;`@path/to/file` נפרש **במלואו** בעת ההפעלה.
- עד **4 רמות** של ייבוא מקונן.
- שורד `/compact` – נטען מחדש אחרי דחיסה.

## ייבוא מול טעינה מותנית – `.claude/rules/`

ייבוא עם `@` נטען תמיד. אם חוק רלוונטי רק לחלק מהקוד, שימו אותו ב־`.claude/rules/` עם `paths:` בכותרת:

<div dir="ltr">

```markdown
---
paths:
  - "src/api/**/*.ts"
---
# חוקי API
- כל endpoint מחזיר `{ data, error }`.
```

</div>

החוק נטען **רק כש־Claude נוגע בקבצים שמתאימים** לתבנית. החל מגרסה 2.1.285, חוקים כאלה נטענים גם בעריכה/כתיבה (Write/Edit) ולא רק בקריאה.

## טיפים

- &rlm;**`/init`** יוצר CLAUDE.md ראשוני – אבל הוא נוטה לתאר את מה שכבר רואים בקוד. ערכו ומחקו בלי רחמים. `CLAUDE_CODE_NEW_INIT=1` מפעיל גרסה אינטראקטיבית שעוברת גם על Skills ו־Hooks.
- &rlm;**`/memory`** פותח את קבצי ה־CLAUDE.md לעריכה.
- **חדש (2.1.283): `/doctor prompt-audit`** – בודק את CLAUDE.md, ה־Skills וה־Agents שלכם ומסמן דפוסי prompting מיושנים. שווה להריץ אחרי כל שדרוג מודל.
- מייבאים מכלי אחר? **`/import codex|gemini|cursor`** מביא קבצי הוראות, MCP ופקודות מ־Codex, Gemini CLI או Cursor.

---

<p align="center"><a href="01-the-stack.md">→ הקודם: מפת העולם</a> &nbsp;|&nbsp; <a href="../README.md">📚 תוכן העניינים</a> &nbsp;|&nbsp; <a href="03-context-memory.md">הבא: הקשר וזיכרון ←</a></p>

</div>
