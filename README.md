# Civic.Social — Ecosystem Architecture

A single-page reference diagram of the Civic.Social ecosystem: the apps people use, the components they're built from, the participant-owned identity and data they rest on, the civic specifications that define the protocol, and the open web standards underneath it all.

**Live diagram:** _add your GitHub Pages URL here once Pages is enabled_

## What's in this repo

- **`Civic Social Ecosystem.html`** — the diagram. Single self-contained HTML file. No build step.
- **`CLAUDE.md`** — context for AI assistants editing this document (architecture, design system, conventions).

## How to view it

Open `Civic Social Ecosystem.html` in any modern browser. That's it.

## How to publish it

This repo is set up to deploy via **GitHub Pages**:

1. Push to `main`
2. In **Settings → Pages**, set source to `main` branch, root folder
3. GitHub publishes the diagram at `https://<owner>.github.io/<repo>/Civic%20Social%20Ecosystem.html` within ~30–60 seconds

## How to embed it on a website

```html
<iframe
  src="https://<your-pages-url>/Civic%20Social%20Ecosystem.html"
  width="100%"
  height="3200"
  style="border:0; max-width:1500px; display:block; margin:0 auto"
  title="Civic.Social Ecosystem Architecture">
</iframe>
```

The diagram is a fixed-width 1440px "sheet" — the iframe `max-width` should be at least that for the design to render without scrolling horizontally. Height is approximate; adjust to fit your layout.

## The architecture, briefly

The diagram is organized as five horizontal bands. **Read bottom-up:**

1. **Open Web Standards** — ActivityPub, DIDs, Verifiable Credentials, OAuth/OIDC. Bedrock.
2. **Civic Specifications** — Civic.Social's own open specs (Hub, Process, Activity, Identity) that extend the standards above.
3. **Sovereign Foundation** — participant-owned identity and data: Citizen, Entity, and Community nodes plus their data stores. Portable, no vendor lock-in.
4. **Components** — reusable building blocks: Activity Feed, Processes, Citizen Console, PDS, Identity Adapter, Access Control. Some ship as standalone embeds.
5. **Interfaces** — the apps people actually use: Civic Hub, Citizen Dashboard, Citizen Account Provider, Representative Space, Badge / Credential Issuer.

See `CLAUDE.md` for the full design system and editing conventions.

## License

_Add your preferred license here (e.g. CC BY 4.0 for the diagram content, MIT for the code)._
