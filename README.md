# EECS 110 — Discover Computer Science · course website

Public course site for **EECS 110: Discover Computer Science** (University of Michigan),
a 2-credit introduction to Python for students with zero prior programming experience.

Live at **<https://eecs110umich.github.io>**.

It is a small [Jekyll](https://jekyllrb.com/) site hosted on **GitHub Pages**. It is built
so that a new instructor each semester can hand it off and update it by editing **one file**.

---

## ⭐ What to change each semester

For a normal semester turnover you edit **exactly one file** plus, optionally, a couple of
images. That's the whole job.

1. **`_data/course.yml`** — every semester-specific value: term (and `term_season`, which
   gates term-specific FAQ entries like the Thanksgiving question), meeting time and room, the
   **weekly calendar** (Mon–Fri events shown on the Schedule page — office hours live here
   now), the current-student links (each with an optional `home: true` to also surface it on
   the homepage), Python resources, staff cards (per-person fields feed the wide card + emoji
   reveals — any blank field is simply omitted), the tagline and `syllabus_url`, and the two
   academic-integrity keys (`academic_integrity_summary` for the site-wide footer,
   `academic_integrity_full` for the `/academic-integrity/` page). Fields marked `TODO` are
   placeholders waiting for a real value; the site builds and looks fine before you fill them.
   Every list (`weekly_calendar`, `links`, `python_resources`, `staff`) can have **any number
   of entries** — add or delete freely.

2. **`assets/img/`** *(only if you want to swap images)* —
   - `banner.jpg` → replace with your own banner (`.jpg`/`.png`); if you change the filename,
     update the `<img src>` in [`index.md`](index.md).
   - `assets/img/staff/` → drop staff photos here and point each `staff:` entry's `photo:`
     field at them. A card with no photo shows a neutral initial avatar, so photos are
     optional.

**Rule of thumb:** if you're about to type a date, URL, name, or room number into a page or
layout, stop — it belongs in `_data/course.yml` instead. Nothing that changes yearly should
be hard-coded anywhere else.

---

## Run it locally

You need **Ruby** and **Bundler**. macOS system Ruby is too old for the current GitHub Pages
gem; install a modern Ruby first (e.g. `brew install ruby`, then make sure its `bin` is on
your `PATH`).

```sh
# one time, from the repo root:
bundle install

# then, to preview with live reload:
bundle exec jekyll serve
```

Open <http://localhost:4000>. The `Gemfile` pins the **`github-pages`** gem so your local
build uses the same Jekyll version GitHub Pages runs — if it builds cleanly here, it builds
there.

---

## How the site is organized

```
_config.yml            Site-wide settings. NOTHING semester-specific here.
_data/course.yml       ← the one file you edit each semester.
_layouts/default.html  Shared shell (left nav + main column + footer) for every page.
_includes/
  nav.html             Left navigation (has a commented slot for a future logo).
  footer.html          Copyright + academic-integrity summary + "Full policy" link.
  link-cards.html      Reusable card grid for {name,url,note} lists.
assets/
  css/style.css        The single hand-written stylesheet. No frameworks, no CDN.
  img/banner.jpg       Banner image (swap for your own).
  img/staff/           Staff photos.
index.md               Home / Overview.
schedule.md            Weekly calendar (Mon–Fri, color-coded pills).
staff.md               Staff cards (wide, with accessible emoji reveals).
resources.md           Course links + Python resources.
faq.md                 Frequently asked questions (in the nav).
academic-integrity.md  Full copyright & integrity policy (footer link, NOT in nav).
```

Every page is Markdown with front matter and renders through `_layouts/default.html`, so the
nav and footer appear on all of them automatically.

### Why this repo is served at the root (link style)

The repo is named **`eecs110umich.github.io`** — exactly `<org>.github.io`. GitHub treats
that as the organization's **site at the domain root**, so `baseurl` is `""` and every
internal link is a plain absolute path like `/staff/`. Do **not** rename the repo or set a
`baseurl`, or the links break.

---

## Hosting & GitHub setup

- **Org:** `eecs110umich` owns this repo (mirroring `eecs183staff` / `eecs281staff`) so the
  site survives instructor turnover instead of living on a personal account. The org's
  "belongs to" field is set to a personal account — that's just GitHub contact metadata and
  grants the university no ownership or control; it does not make this an official U-M org.
- **Pages:** Settings → Pages → **Build from branch → `main` / root**. Do **not** add a
  `.nojekyll` file — Jekyll must run.

### Handoff checklist (do this before an instructor leaves)

A GitHub org can have several **Owners**, and the org + repo persist independently of any one
personal account, so **no repo transfer is ever needed**.

- [ ] Add the successor (or a stable co-instructor/TA) as a **second Owner** of the
      `eecs110umich` org — *do this as soon as a second person exists.* A solo-owner org is a
      single point of failure.
- [ ] Add each new semester's instructor as an org **member**.
- [ ] The departing instructor can then step down as Owner or leave the org.

---

## Deliberately out of scope (please don't "helpfully" add these)

- **Assignments / assignment writeups.** Intentionally omitted; everything assignment-related
  stays on **Canvas**. This is policy, not an oversight, for two reasons: (a) mirroring Canvas
  is ongoing work for a solo instructor without a TA team, and (b) in the LLM era, publicly
  posting a solo-taught course's assignments makes them trivial to feed to a model and
  expensive to re-author every term. Keep them off the public site.
- **Dated semester schedule.** The site shows only the typical-week "at a glance"; detailed
  dates live on Canvas. No per-week table.
- **Course logo.** None yet. `_includes/nav.html` has a clearly-marked slot to drop one in
  later without a redesign.
- **Custom domain.** The site ships on `eecs110umich.github.io`. To move to something like
  `eecs110.eecs.umich.edu` later: add a `CNAME` file containing the domain, create the DNS
  record (a `CNAME` pointing at `eecs110umich.github.io`), and set the custom domain under
  Settings → Pages. A `.eecs.umich.edu` subdomain would need **EECS IT** to create the DNS
  record. Don't buy a domain or touch DNS unless you're actually doing this.

---

## Conventions for anyone editing the code

- All semester content comes from `_data/course.yml`. Layouts and pages describe the course
  in general terms (that copy doesn't change yearly); specifics come from the data file.
- Dependencies stay limited to the **`github-pages`** gem. No JS frameworks, no CDN links, no
  external fonts unless self-hosted under `assets/`. The site embeds **zero** third-party
  assets — every stylesheet and image is served from this repo. (Outbound links to course
  tools like Canvas or Piazza are fine; the rule is about *embedded* resources.) Keep it that
  way for privacy and reliability.
- Keep it accessible: alt text on images, real `<nav>`/`<main>` landmarks, sufficient
  contrast.
