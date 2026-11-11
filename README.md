# danielfrenkel.com

Daniel Frenkel's author site. GitHub Pages builds it with Jekyll from the `main`
branch and serves it at danielfrenkel.com (see `CNAME`). There is nothing to install
and no build step to run: commit a change, and the site updates a minute or two later.

## Add a post

1. In the repo on GitHub, go into the **`_posts`** folder and choose
   **Add file → Create new file** (or upload a `.md` file you wrote elsewhere).
2. Name the file with the date first, then a short slug:

   ```
   2026-11-14-the-drive-home.md
   ```

   The date in the name is the post's date. The slug becomes its address:
   `danielfrenkel.com/writing/the-drive-home/`.
3. Start the file with a title block, then write the post in Markdown:

   ```markdown
   ---
   title: The Drive Home
   ---

   First paragraph of the post.

   ## A subheading

   More text. *Italics*, **bold**, [links](https://example.com) and
   > block quotes all work.
   ```

   Optional: add `description: One sentence for search results and link previews.`
   under the title. Without it, the post's first paragraph is used.
4. Commit. The post shows up on the Writing page (newest first) and in the
   three latest on the home page, with the subscribe box at the end of it.

Notes:

- The folder must be called `_posts`, with the underscore. Jekyll only treats
  files there as posts.
- A post dated in the future stays hidden until that date has passed **and** the
  site is rebuilt by a later commit.
- To take a post down, delete its file.

## Change other things

| What                                  | Where                                       |
|---------------------------------------|---------------------------------------------|
| The line under your name (home page)  | `tagline` in `_config.yml`                  |
| Substack address for the subscribe box | `substack_url` in `_config.yml`            |
| Subscribe box: Substack's box or a plain button | `subscribe_style` in `_config.yml` (`embed` or `button`) |
| Book titles, descriptions, links, order | `_data/books.yml`                         |
| Contact page                          | `contact/index.html`                        |
| Crisis-lines page                     | `resources/index.html`                      |
| Colors, fonts, spacing                | `assets/css/site.css`                       |
| Header and footer on every page       | `_layouts/default.html`                     |
| Subscribe box                         | `_includes/subscribe.html`                  |

## What the site loads

Everything is served from this repo, including the Literata font
(`assets/fonts`, SIL Open Font License, see `OFL.txt`). There are no analytics,
trackers, cookies or font services of its own. The only outside service is the
subscribe box, and what it loads depends on `subscribe_style`:

- `embed`: Substack's own sign-up box, in a frame. Substack's code runs in it,
  and in testing it also loaded Google's tag-manager and ad tags, Cloudflare
  Insights, Datadog and Sentry.
- `button`: a heading, one line and a Subscribe button that opens the Substack
  sign-up page. Nothing from Substack loads until a reader taps it.

## Hosting

- Repo → Settings → Pages: deploy from branch `main`, folder `/ (root)`;
  custom domain `danielfrenkel.com`, **Enforce HTTPS** on.
- DNS at Namecheap: four `A` records for `@` (185.199.108.153, 185.199.109.153,
  185.199.110.153, 185.199.111.153) and a `CNAME` for `www` →
  `daniel-frenkel.github.io`.
- Mail to contact@danielfrenkel.com is forwarded by Namecheap's free email
  forwarding.
- The old addresses `/books.html`, `/contact.html` and `/resources.html`
  redirect to the new pages.
