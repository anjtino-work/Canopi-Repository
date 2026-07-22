# Team repository (static HTML)

A plain HTML/CSS/JS internal site: SOPs, Knowledge Base, Projects, Meetings, Resources, Tools, and Team Spaces. No backend, no build step — just files.

## Deploying with GitHub Pages

1. Push this repo (or upload these files) to a GitHub repository.
2. Go to the repo's **Settings > Pages**.
3. Under "Build and deployment", set Source to **Deploy from a branch**, branch `main`, folder `/ (root)`.
4. Save. GitHub gives you a URL like `https://yourorg.github.io/repo-name/` within a minute or two.
5. The included `.nojekyll` file tells GitHub Pages to serve the files as-is (this site isn't using Jekyll).

## Structure

```
index.html                 Homepage dashboard
knowledge-base/             SOPs, process docs, policies, best practices, FAQs
projects/                   Active/completed projects, templates, docs
meetings/                   Leadership/team meetings, minutes, action items
resources/                  Templates, forms, checklists, brand assets
tools/                      Internal applications, user guides, system docs
team-spaces/                Executive, Product, Engineering — each with
                             Documentation / Meeting Notes / Decisions / Shared Resources
partials/                   Shared header/footer, injected via assets/js/main.js
assets/css/theme.css        Site-wide theme (white + dark purple)
assets/js/main.js           Partial includes, client-side search, recently viewed
assets/js/search-index.json Manually maintained list of pages for search — add a
                             line here whenever you add a new page you want findable
```

## Adding content

There's no CMS — add a new page by copying an existing one in the relevant folder (e.g. copy `knowledge-base/sops/example-sop.html` for a new SOP), edit the text, and add a link to it from that section's `index.html` and to `assets/js/search-index.json`.

## What's deliberately NOT here

- **1-on-1 meeting summaries.** These need real per-user privacy (an employee sees only their own; a manager sees only their direct reports') that a static site with no login and no backend cannot provide. Don't add these here — keep them out until there's a real backend (e.g. the Power Pages/Dataverse version) that can enforce that access control properly.
- **Real editable shared documents.** This site can link OUT to documents that live in Google Drive/OneDrive/SharePoint, but it can't host live co-editable files itself. Put links in `resources/index.html` pointing to wherever those documents actually live.
- **Per-person accounts, permissions, or private content of any kind.** Everything in this repo is visible to anyone with the URL, since GitHub Pages has no login layer by default. Don't put anything here that shouldn't be visible to the whole company (or the public, if the repo is public).

## Known limitations vs. the Power Pages version

- Search is a simple client-side keyword match against `search-index.json` — not full-text search across page content.
- "Recently viewed" and any favorites use the browser's local storage — personal to that browser/device, not synced across devices, and not visible to anyone else (including admins).
- No approval workflow — anyone with write access to the repo can publish directly. Use pull requests and required reviewers in GitHub's branch protection settings if you want a review step before changes go live.
