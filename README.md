# testrepo — Claude-run content/affiliate site

Scaffold for a niche content + affiliate site, built with [Eleventy](https://www.11ty.dev/) and deployed via GitHub Pages. Content, publishing, monitoring, and the cost/revenue ledger (`ledger.md`) are maintained by scheduled Claude runs; legal/financial/account setup stays with the human owner. Full background and rules of engagement: see the plan this was built from (kept outside this repo, by the business owner).

## Status

- [x] Site scaffold (Eleventy config, base layout, legal page templates, GitHub Actions deploy workflow, ledger).
- [x] **Niche chosen: Homeoffice-Einrichtung (home office setup, ergonomics, and German tax deductions for remote work).** German-language, avoids YMYL medical/financial-advice territory, has real Amazon.de affiliate potential (desks, monitor arms, chairs), and is less saturated than English-language home-office content. First 2 articles published; more added on each scheduled run.
- [ ] One-time human setup (below) not yet confirmed complete.

## One-time human setup checklist

1. **Gewerbeanmeldung** at your local Gewerbeamt.
2. **Finanzamt tax questionnaire (ELSTER)** — elect Kleinunternehmerregelung (§19 UStG).
3. **IHK fee exemption application** ("Antrag auf Beitragsbefreiung für Existenzgründer").
4. **Custom domain** (optional at first — `github.io` subdomain works to start) — if you buy one, add a `CNAME` file in `src/` and configure DNS.
5. **Enable GitHub Pages**: repo Settings → Pages → Source → **GitHub Actions**. (One click; the workflow in `.github/workflows/deploy.yml` handles the rest on every push to `main`.)
6. **Ad/affiliate accounts** (Google AdSense, Amazon Partnernet, etc.) — once approved, hand over the embed snippet(s)/publisher IDs so they can be wired into `src/_includes/base.njk` and `src/_data/site.json`.
7. **Google Search Console + Analytics** for the domain, with read-only API access granted, so traffic data can be pulled automatically instead of manually reported.
8. **Fill in the real legal details** in `src/impressum.md` and `src/datenschutz.md` (currently placeholder `[Vorname Nachname]` etc.) once your Gewerbe/Finanzamt registration is done.

## Local development

```bash
npm install
npm run serve
```

## Structure

```
src/
  _data/site.json      site title/description, adsense/affiliate IDs
  _includes/           base layout + post layout
  posts/               markdown articles (one file per post)
  index.njk            homepage / post listing
  impressum.md          datenschutz.md   legal pages (German requirement)
ledger.md              cost vs. revenue tracking, updated every scheduled run
```
