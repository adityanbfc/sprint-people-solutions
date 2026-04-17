# Sprint People Solutions — Website Guide

Your website is a single file: **index.html**. No server, no database, no framework. Open it in any text editor — Notepad on Windows, TextEdit on Mac, or VS Code (free, recommended) — make your change, save, and refresh in a browser.

**Tip:** In any text editor, press Ctrl+F (Windows) or Cmd+F (Mac) to search. Every editable section is marked with a comment like `<!-- EDIT: ... -->` so you can find things instantly.

---

## 1. Changing any text

### Headline, sub-lines, body paragraphs
Find the `<!-- EDIT: ... -->` comment above the line you want to change. The text to edit always sits between a `>` and a `<` — for example:

```html
<h1 class="hero-h1 ...">Because great hiring should move fast — and right.</h1>
```

Change only the words between `>` and `</h1>`. Never remove the tags.

### Bullet points (Services section)
Each bullet looks like:
```html
<li>Mid to senior hiring</li>
```
Edit the text, copy the line to add a bullet, or delete the whole line to remove one.

### Ticker text (the scrolling band)
Search for `ticker-item`. You'll see three identical `<span>` blocks. Change all three to the same text — they must match for the loop to work.

---

## 2. Updating the email address

Search for `shreya@sprintpeople.in` — it appears four times. Each instance looks like:

```html
<a href="mailto:shreya@sprintpeople.in">shreya@sprintpeople.in</a>
```

Update **both** parts every time:
1. The address after `mailto:` — what opens when someone clicks
2. The text between `>` and `</a>` — what they see on screen

---

## 3. Setting up the contact form (Formspree)

The "Start a conversation" button opens a form. To receive submissions by email, connect it to Formspree — a free service.

**Step 1.** Go to **formspree.io** and create a free account using shreya@sprintpeople.in.

**Step 2.** Click **+ New Form**. Name it "Sprint Website". Confirm your email when Formspree sends a verification link.

**Step 3.** After confirming, you'll see your form endpoint:
```
https://formspree.io/f/xabc1234
```
The code at the end (`xabc1234`) is your form ID.

**Step 4.** Open index.html and search for `YOURFORMID`. You'll find:
```
fetch('https://formspree.io/f/YOURFORMID', {
```
Replace `YOURFORMID` with your actual ID:
```
fetch('https://formspree.io/f/xabc1234', {
```
Save the file.

**Step 5.** Test it — open the site, click "Start a conversation", fill and submit the form. You should get an email within a minute.

---

## 4. Connecting the form to Google Sheets (Zapier)

Once Formspree is live, you can log every submission to a Google Sheet automatically.

**Step 1.** Create a Google Sheet with these column headers in row 1:
```
Name | Company | Email | Phone | Need | Message
```

**Step 2.** Go to **zapier.com** and create a free account.

**Step 3.** Click **+ Create** → **Zap**.

**Step 4.** Set the **Trigger**:
- App: Formspree
- Event: New Submission
- Connect your Formspree account and choose the Sprint Website form

**Step 5.** Set the **Action**:
- App: Google Sheets
- Event: Create Spreadsheet Row
- Connect your Google account, select your sheet, and map each Formspree field to the matching column

**Step 6.** Click **Test** — submit the form on your site, then come back and click "Test trigger" in Zapier. If it finds the submission, click **Publish**. Done — every new submission creates a new row automatically.

---

## 5. Adding your LinkedIn link to the footer

Search for `LINKEDIN` in the file. You'll find:

```html
<!-- LINKEDIN: Uncomment and add your profile URL when ready
     <a href="https://linkedin.com/in/YOUR-PROFILE">LinkedIn</a>
-->
```

To activate:
1. Delete `<!--` on the first line
2. Delete `-->` at the end
3. Replace `YOUR-PROFILE` with your actual LinkedIn path

Result:
```html
<a href="https://linkedin.com/in/shreyasharma">LinkedIn</a>
```

---

## 6. Activating Phase 2 — JD–CV Match Tool

Search for `PHASE 2`. You'll find:

```html
<!-- PHASE 2: Uncomment when JD–CV Match Tool is live -->
<!-- <a href="/match">JD–CV Match</a> -->
```

Remove the `<!--` and `-->` from the inner line only, then replace `/match` with the real URL:

```html
<!-- PHASE 2: Uncomment when JD–CV Match Tool is live -->
<a href="https://your-tool-url.com">JD–CV Match</a>
```

---

## 7. Activating Phase 3 — Open Mandates

Search for `PHASE 3`. Same process:

```html
<!-- PHASE 3: Uncomment when Open Mandates page is live -->
<!-- <a href="/mandates">Open Mandates</a> -->
```

Remove the comment markers from the inner line and update the URL:

```html
<a href="https://your-mandates-url.com">Open Mandates</a>
```

---

## 8. Updating the copyright year

Search for `copyright year`. Change `2026` to the new year.

---

## 9. Publishing the site

Upload index.html to any static host. The easiest free options:

- **Netlify Drop** — drag the file to app.netlify.com/drop, get a URL in 30 seconds
- **Vercel** — upload at vercel.com or connect a GitHub repository
- **GitHub Pages** — free hosting from a GitHub repo

No backend needed. The file is fully self-contained.

---

## Before you edit: make a backup

Duplicate index.html and rename it `index-backup-[date].html` before touching anything. If something breaks, you can restore it in seconds.
