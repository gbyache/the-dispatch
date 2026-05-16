# The Dispatch — Weekly Workflow
## WORKFLOW.md v1.0

---

## EVERY SUNDAY — Update & Deploy (15 minutes)

### Step 1 — Open Claude Code
Start a new session. Say: "Let's do the Dispatch weekly update."

Claude will:
- Write 6 new posts for the coming week (3 Michael, 3 Wolf & Pigeons)
- Add them to `WEEK_POSTS` in `index.html` under the new week key
- Deploy to Netlify automatically

No manual file editing. No drag and drop. One command.

---

### Step 2 — Review the posts (optional)
Claude will show you all 6 posts before deploying. If anything needs adjusting — topic, tone, a detail to add — say so and it will revise.

If you have a specific angle in mind for any post that week (a current event, a brand story in the news, a Mikey's update), mention it before Claude writes. That context makes the posts sharper.

---

### Step 3 — Deploy
Claude runs:
```bash
cd "/Users/michaellawanson/Documents/Linkedin Post app" && npx netlify-cli deploy --prod --dir .
```

Done. Posts are live on the app.

---

## EVERY POSTING DAY

### Monday 8–9 AM
1. You receive a push notification: "Time to post — Michael Lawanson"
2. Open The Dispatch app on your phone
3. Tap **Michael** tab → tap **Copy** on Post 1
4. Open LinkedIn → paste → post
5. Tap **✓** on the card to mark it done

### Wednesday 12 PM
1. Notification: "Time to post — Wolf & Pigeons"
2. Open The Dispatch → tap **Wolf & Pigeons** tab → Copy Post 2
3. Post on the Wolf & Pigeons LinkedIn page
4. Tap **✓**

### Friday 9 AM
1. Notification: "Friday post — The Dispatch"
2. Check the dashboard to see which Friday slot is up
3. Copy and post accordingly
4. Tap **✓**

---

## IF SOMETHING BREAKS

| Problem | Fix |
|---------|-----|
| Posts are empty in the app | App needs redeployment. Run the deploy command or ask Claude. |
| Notifications not arriving | Check ntfy app — must be subscribed to `thedispatch-lawanson`. Check iPhone Focus/DND settings. |
| Wrong channel in settings | Open app → Settings tab → update channel to `thedispatch-lawanson` → Save |
| Need to redeploy manually | `cd "/Users/michaellawanson/Documents/Linkedin Post app" && npx netlify-cli deploy --prod --dir .` |
| Week number looks wrong | The app calculates week number automatically. If it looks off, ask Claude to verify. |

---

## FILE LOCATIONS

| File | Path |
|------|------|
| App (HTML) | `/Users/michaellawanson/Documents/Linkedin Post app/index.html` |
| Notification config | `/Users/michaellawanson/Documents/Linkedin Post app/dispatch.config` |
| Monday reminder skill | `/Users/michaellawanson/Documents/Claude/Scheduled/dispatch-remind-monday/SKILL.md` |
| Wednesday reminder skill | `/Users/michaellawanson/Documents/Claude/Scheduled/dispatch-remind-wednesday/SKILL.md` |
| Friday reminder skill | `/Users/michaellawanson/Documents/Claude/Scheduled/dispatch-remind-friday/SKILL.md` |
| These specs | `/Users/michaellawanson/Documents/Linkedin Post app/specs/` |

---

## DEPLOYED URL

**https://spiffy-seahorse-31e151.netlify.app**

This is the URL saved to your iPhone home screen as "The Dispatch."
