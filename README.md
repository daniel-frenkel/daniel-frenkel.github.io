# danielfrenkel.com — deploy checklist

Static site for GitHub Pages. Repo: https://github.com/daniel-frenkel/danielfrenkel.github.io

## One naming fix (recommended, 30 seconds)

Your GitHub username is `daniel-frenkel` (with a hyphen), so the special "user site" repo
name is **`daniel-frenkel.github.io`** — the repo you created (`danielfrenkel.github.io`)
doesn't match, which makes it an ordinary project repo. Everything still works with the
custom domain either way, but the rename is cleaner:

- Repo → Settings → General → Repository name → change to `daniel-frenkel.github.io` → Rename.

If you skip the rename, just make sure Pages is enabled (step 2) — the custom domain does
the rest.

## 1. Upload the site (no git client needed)

In the repo: **Add file → Upload files** → drag in all six files
(`index.html`, `books.html`, `resources.html`, `contact.html`, `CNAME`, this `README.md`)
→ Commit changes to `main`.

## 2. Turn on Pages

Repo → Settings → Pages:
- Source: **Deploy from a branch** → Branch: `main`, folder `/ (root)` → Save.
- Custom domain: enter `danielfrenkel.com` → Save.
- Check **Enforce HTTPS** once it becomes available (after DNS propagates — minutes to a
  few hours).

## 3. Namecheap DNS (Domain List → danielfrenkel.com → Advanced DNS)

Delete the parking records, then add:

| Type  | Host | Value                      |
|-------|------|----------------------------|
| A     | @    | 185.199.108.153            |
| A     | @    | 185.199.109.153            |
| A     | @    | 185.199.110.153            |
| A     | @    | 185.199.111.153            |
| CNAME | www  | daniel-frenkel.github.io   |

Note the CNAME value uses your **username** (`daniel-frenkel.github.io`), not the repo
name — that's correct either way.

## 4. Free email — no fee, ever

This is forwarding, not a mailbox, and Namecheap includes it free:

- Domain List → danielfrenkel.com → **Redirect Email** (or Advanced DNS → Mail Settings →
  **Email Forwarding**).
- Add: `contact` → forwards to → `danielfrenkel@gmail.com`.
- Namecheap sets the needed MX records automatically when you choose Email Forwarding.
  Don't add MX records by hand, and don't delete the ones it creates.

Mail to contact@danielfrenkel.com now lands in your Gmail. You reply from your Gmail
address, which is fine for reader mail. If you ever want replies to come *from* the
domain, Namecheap Private Email is about $12/year — a later decision, not a monthly fee,
and not needed now.

## 5. Before or after deploying — your pass

- All site copy is my draft in your register: edit anything, especially the home-page
  bio lines.
- The Writing link points to `https://danielfrenkel.substack.com` in all four pages —
  correct it if your Substack address differs (find-and-replace across the files).
- The contact address on the page is assembled by a small script so scrapers reading the
  raw HTML don't harvest it; the `<noscript>` fallback shows it spelled out.

## Later, if contact volume ever justifies a real form

Formspree or Web3Forms: one HTML `<form>` block pasted into `contact.html`, posting to
their endpoint — they filter spam and email you submissions. No rebuild, no backend.
Not worth the dependency until the mail volume exists.

## Ch12 P.S.

Once this is live, the manuscript placeholder can read: **danielfrenkel.com** — readers
will find the contact address there.
