# lianagizatulina.com

Personal site, served by GitHub Pages from this repo. Two doors: thirty seconds if you're screening, ten minutes if you
want to know whether I'm real.

## How it's built

Plain HTML and one stylesheet. No framework, no static-site generator, no
build step. `git push` is the deploy.

JavaScript appears on exactly one page, as progressive enhancement and
nothing else: the error-budget bar on the observability page renders its
real values in HTML, and the script only adds the slider on top. With
scripting disabled the page is complete — you lose the ability to drag,
not the content.

That's a deliberate choice rather than a shortcut. The site's job is to get one
project page read, and every layer between writing and shipping is a tax on
that. It also means the site works with JavaScript disabled, in a screen
reader, in a link preview, and on a bad phone connection — which a portfolio
that a recruiter opens on the train actually needs.

The site's own build showcases nothing on purpose. The projects are the
portfolio; this is a fast, legible way to read them.

## Layout

```
index.html              landing — header card, two doors, three numbers
30-seconds.html         door 1 — condensed resume, stack, contact
projects/index.html     door 2 — project index
projects/*.html         one page per project
style.css               all styles, light and dark
.nojekyll               serve files as-is; skip Jekyll processing
```

## Conventions

- **Every project page follows five beats**, in this order: what it is · scope
  and ownership · what changed (each number with one line of method) · how it
  works · what went wrong. The failure section comes last — wins and
  architecture carry the page.
- **One inspectable artifact per page.** Ten-ish lines of real, syntax-
  highlighted work, inline. Not a repo link.
- **Diagrams are hand-authored inline SVG** with real `<title>` and description
  text, so they survive a screen reader and don't cost a page-weight budget.
- **No employer names**, here or on the project pages. What was built, what
  changed, how it works, what went wrong.
- **The project index lists only pages that exist.** No placeholder tiles, no
  "coming soon."

## Deploying

GitHub Pages serves `main` at the repository root. Settings → Pages → Source →
Deploy from a branch → `main` / `/ (root)`.

### Custom domain

1. Point DNS at GitHub. On Cloudflare a single flattened `CNAME` at the apex
   to `liana-giza.github.io` works, plus the same for `www` — both set to
   **DNS only**, never proxied, or the certificate cannot be issued.
2. Settings → Pages → Custom domain. This commits a `CNAME` file here.
3. Tick **Enforce HTTPS** once the certificate provisions.
4. Verify the domain under account settings → Pages → verified domains. Without
   this, a deleted or renamed repo leaves the domain claimable by someone else.

## Checks before shipping a page

- Reads on a phone with no horizontal scroll.
- Landing under a second on 4G; no layout shift.
- Legible in both light and dark.
- Every claim on the page is one I can defend under follow-up questions.
