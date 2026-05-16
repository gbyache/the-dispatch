# The Dispatch — Project Spec
## SPEC.md v1.0

---

## 1. WHAT IT IS

A mobile-first PWA (Progressive Web App) saved to Michael Lawanson's iPhone home screen. It holds the week's LinkedIn posts for two pages, lets you copy them with one tap, and sends push notifications on posting days.

**What it is not:** A post generator. Not a scheduler. Not a social media tool. It is a copy-and-post interface — the posts live inside the app, you copy them, you open LinkedIn, you paste.

---

## 2. THE TWO PAGES

| Page | Type | Voice |
|------|------|-------|
| Michael Lawanson | Personal LinkedIn | Brand strategist. Thoughtful, observational, declarative. No fluff. |
| Wolf & Pigeons | Agency LinkedIn | Sports and entertainment brand design. Industry critique. Design craft. |

---

## 3. POST SCHEDULE

| Day | Time | Page | Pillar |
|-----|------|------|--------|
| Monday | 8–9 AM | Michael Lawanson | Strategy & Design |
| Wednesday | 12 PM | Wolf & Pigeons | Industry Reaction |
| Friday | 9 AM | Alternating | Michael = Mikey's Gourmet Chin Chin / W&P = Brand Philosophy or Design Craft |

6 posts per week total. 3 per page.

---

## 4. TECH STACK

| Layer | Tool | Notes |
|-------|------|-------|
| App | Single HTML file (`index.html`) | All JS/CSS inline. No build step. |
| Hosting | Netlify | Site: `spiffy-seahorse-31e151.netlify.app` |
| Storage | localStorage | Keyed by week ID + page + slot. Resets each new week automatically. |
| Notifications | ntfy.sh | Channel: `thedispatch-lawanson` |
| Deploy CLI | netlify-cli (npx) | Already linked and authenticated |

---

## 5. HOW POSTS GET INTO THE APP

Posts are baked directly into `index.html` as a JavaScript constant called `WEEK_POSTS`, keyed by ISO week ID (e.g. `2026-W21`). When a card is empty (no localStorage entry), it auto-fills from the matching week's default post.

The app never calls an API. Posts are written by Claude each Sunday, added to `WEEK_POSTS`, and deployed. User opens the app Monday — posts are already there.

---

## 6. NOTIFICATION SYSTEM

Scheduled reminders run via Claude Code skills:

| File | Fires | Message |
|------|-------|---------|
| `dispatch-remind-monday/SKILL.md` | Monday 9 AM | Post time — Michael Lawanson |
| `dispatch-remind-wednesday/SKILL.md` | Wednesday 12 PM | Post time — Wolf & Pigeons |
| `dispatch-remind-friday/SKILL.md` | Friday 9 AM | Post time — Friday slot |

All reminders curl `https://ntfy.sh/thedispatch-lawanson` using the channel stored in `dispatch.config`.

The ntfy app on Michael's iPhone must be subscribed to `thedispatch-lawanson` to receive them.

---

## 7. DEPLOY COMMAND

```bash
cd "/Users/michaellawanson/Documents/Linkedin Post app" && npx netlify-cli deploy --prod --dir .
```

No login needed. Already linked to `spiffy-seahorse-31e151`.

---

## 8. OUT OF SCOPE

- Auto-posting to LinkedIn (against platform TOS)
- Post analytics or engagement tracking
- Multiple users or shared access
- Any paid tools or API keys
