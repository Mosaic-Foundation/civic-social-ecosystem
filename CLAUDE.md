# CLAUDE.md — Civic.Social Ecosystem Diagram

Context for any AI assistant editing this project.

## What this is

A single self-contained HTML document that visualizes the Civic.Social ecosystem architecture as a stack of five horizontal bands. Designed to be read **bottom-up** (web standards as bedrock → interfaces at the top). It is a reference / explainer artifact, not an app.

The whole document is one file: **`Civic Social Ecosystem.html`**. Inline CSS, no build step, no JavaScript dependencies, no framework. Google Fonts (Libre Franklin + Inter) are loaded via `<link>` from `fonts.googleapis.com`. Deploy by serving the file statically.

## Architectural model the document describes

Five bands, in source order (top of document to bottom of document):

1. **Interfaces** — distinct apps people use. Civic Hub, Citizen Dashboard, Citizen Account Provider, Representative Space, Badge/Credential Issuer. Each lists "Assembled from" tiles showing which Components it composes.
2. **Components** — reusable building blocks. Activity Feed (with five lenses: Inbox, Notifications, Discovery, Hub View, Embed), Processes, Citizen Console, PDS, Identity Adapter, Access Control. Two are "shippable as embed" (marked with a ✦ pip).
3. **Sovereign Foundation** — participant-owned identity + data. Three rows: Citizen (Citizen Node + Personal Data Store), Entity (Entity Node + Entity Data Store), Community (Community Node + Community Data Store). Each row has an owner-mark glyph in the left column.
4. **Civic Specifications** — Civic.Social's own open specs. Hub Spec, Process Spec, Activity Spec, Identity Spec. These extend the standards below.
5. **Open Web Standards** — external bedrock. ActivityPub, DIDs, Verifiable Credentials, OAuth 2.0 / OIDC.

Between bands are **interludes**: a thin rule, a circular pip with ↑, and an italic caption describing the upward dependency relationship. All arrows point up because the document reads bottom-up.

## Design system

### Palette (earth tones, defined as CSS custom properties in `:root`)

- `--green` `#386759` — primary, used for hubs / community scope
- `--teal` `#294B52` — accent 1, used for components / general ink
- `--rust` `#C37B51` — accent 2, used for citizen/entity scope and the ".Social" dot
- `--yellow` `#EDC572` — accent 3, used for issuer scope
- `--paper` `#F0EBE1` — page background (warm off-white)
- Each band has a tinted background (`--band-*-bg`) and matching edge color (`--band-*-edge`)
- A faint hand-drawn topographic SVG pattern is the body background

### Typography

- **Libre Franklin** — display / titles / lede (weights 400, 500, 600, 700, 800)
- **Inter** — body, labels, micro-copy (weights 400, 500, 600, 700)
- Eyebrow labels: 12px, 700, uppercase, 0.14em–0.16em tracking
- Card titles: 22px, 800, Libre Franklin, tight letter-spacing (-0.015em)
- Body copy: ~14.5px, line-height 1.6

### Card scopes

Cards carry a `data-scope` attribute that paints a 4px colored top stripe:
- `green` → hubs / community
- `teal` → components / general
- `rust` → citizen / entity
- `yellow` → issuers
- `neutral` → external standards

### Recurring patterns

- **`.card-kicker`** — a pill above the title with the scope ("community-scoped", "component · embedded", etc.)
- **`.assembly`** block — bottom of every interface card, lists composed components as tiles
- **`.tile`** — small label inside an assembly, has variants via `data-k` (e.g. `wallet` for rust-toned tiles)
- **`.embed-pip`** — small "✦ shippable as embed" badge for Components that work standalone
- **`.owner-mark`** — the icon column on the left of each Sovereign Foundation row

## Editing conventions

- **Keep the file singular.** Don't split into separate CSS or JS files unless there's a strong reason — the artifact's value is being one self-contained file someone can drop anywhere.
- **All arrows point up.** The document reads bottom-up; the interlude pips and caption phrasings reflect that. If you change a caption, keep the upward grammar ("X above … the Y below").
- **Vocabulary.** Use *Access Control* (not "Authz Seam", not "RBAC"). Use *participants* / *citizens* / *entities* / *communities*. Use *spec* (not "protocol") for Civic.Social's own definitions; *standard* for external W3C/IETF work.
- **Adding a card.** Copy an existing card with the same scope, keep the kicker → title (with optional `.sub`) → description → assembly/tiles structure. Match the surrounding band's grid placement.
- **Adding a band.** Add a new `<section class="band band--X">`, define `--band-X-bg` / `--band-X-edge` in `:root`, add a paired interlude before it.
- **Comment anchors.** Preserve any `data-comment-anchor` attribute when restructuring elements — it pins user review comments to specific nodes.
- **Screen labels.** Each band has a `data-screen-label` (e.g. `"Band Components"`). Keep these on bands so reviewers can reference them.

## Deployment

The file is deployed via GitHub Pages on push to `main`. To embed elsewhere, use:

```html
<iframe
  src="https://<your-pages-url>/Civic%20Social%20Ecosystem.html"
  width="100%" height="3200" style="border:0; max-width:1500px"
  title="Civic.Social Ecosystem Architecture"></iframe>
```

If you make the page narrower or wider, adjust the iframe height — the sheet is fixed at 1440px wide. A future improvement could be a small `postMessage` resize script.

## What this file is NOT

- Not interactive — no clicks, no JS state
- Not responsive — fixed 1440px sheet, intentional for a poster-like reference
- Not a slide deck — single long page
- Not a marketing site — explainer for the team / collaborators
