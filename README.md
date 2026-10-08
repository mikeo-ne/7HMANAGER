# 7HMANAGER

7H Manager is the internal management app for 7H Music Group (Kampala, Uganda): artist roster and contracts, the release planner, the A&R demo inbox, and strategy playbooks.

The whole app is one static file, `index.html`. There is no build step. Tailwind CSS (browser build 4.3.3) and Lucide icons (1.53.0) load from jsDelivr, and fonts load from Google Fonts.

## Deploy on Vercel

1. Import this repository in Vercel.
2. Framework preset: **Other**. Leave the build command empty and the output directory as the default, so Vercel serves `index.html` from the repository root.
3. Open the deployment over HTTPS. PIN hashing uses the Web Crypto API, which only runs in a secure context (HTTPS or localhost).

## Local preview

```bash
python3 -m http.server 8765
```

Then open http://localhost:8765/index.html.

## First run: read this

- **Default PIN: `7H2026`.** Change it straight away in Settings. The default is visible in the source, so the PIN gate is a convenience lock for internal use. It is not server-side authentication.
- **Data stays in the browser.** Records are kept in localStorage. Use Settings → Download backup (JSON) regularly, because clearing site data erases everything.
- **Placeholders to replace:** artist streaming links (search URLs for now), bios, genre tags, and the distributor and radio contacts in the directory. Check every contact before you rely on it.
- The split sheet and agreement are working documents, not legal advice.
