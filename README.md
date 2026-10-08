# 7HMANAGER

7H Manager is the internal management app for 7H Music Group (Kampala, Uganda): artist roster and contracts, the release planner, the A&R demo inbox, and strategy playbooks.

The whole app is one static file, `index.html`. There is no build step. Tailwind CSS (browser build 4.3.3) and Lucide icons (1.53.0) load from jsDelivr, and fonts load from Google Fonts.

## Deploy on Vercel

1. In Vercel, create a new project under the **mike-1-ne** team and import `mikeo-ne/7HMANAGER`.
2. Framework preset: **Other**. Leave the build command empty and the output directory as the default, so Vercel serves `index.html` from the repository root.
3. Settings → Git → **Production Branch**: `arena/b32710e6-7hmanager`. The default branch (`main`) holds only the README, so a production deployment from it returns 404.
4. Settings → Deployment Protection: choose **All Deployments** with **Vercel Authentication**. Standard Protection leaves production domains open, so the production URL would be public. Vercel Authentication and All Deployments are included on every plan.
5. Team access: invite each person to the Vercel team with at least the **Viewer** role. They sign in with their Vercel account to open the app. Anyone else who opens the link can request access, and a team owner, member, admin or developer can approve it.
6. Open the deployment over HTTPS. PIN hashing uses the Web Crypto API, which only runs in a secure context (HTTPS or localhost).

Deployment Protection is a Vercel project setting, not a file in this repository.

## Local preview

```bash
python3 -m http.server 8765
```

Then open http://localhost:8765/index.html.

## Starter data

The app opens with starter records checked against public sources. Every source and its confidence level is listed in [DATA-SOURCES.md](DATA-SOURCES.md).

- **Roster:** Baranga, Mr Fallback, Smokie Cee and Mike 1ne. The team needs to confirm these names. Only Baranga has a bio (drafted from Apple Music) and a streaming link.
- **Catalogue:** three released entries for Baranga, with release dates from Apple Music.
- **Directory:** 16 public organisations covering distribution, pitching, rights bodies (UPRS and URSB), Kampala radio frequencies and streaming platforms.
- **Left for the team:** contract status (every artist starts as Draft), term dates, demo submissions, split sheets, upcoming releases, private roster notes, and label contact details.

Settings → **Restore starter data** replaces everything in the browser with these records.

## First run

- **Change the default PIN (`7H2026`) in Settings straight away.** The default is in the source, so the PIN gate is a convenience lock for internal use, not server-side authentication. Vercel sign-in and the app PIN are separate layers.
- **Data stays in each browser.** Records live in localStorage. Use Settings → Download backup (JSON) regularly, because clearing site data erases everything.
- **Check every contact before outreach.** Directory entries are public organisation details and may change.
- The split sheet and agreement are working documents, not legal advice.

## Browsers with the first version's sample data

A browser that still holds the first version's sample records is migrated on its next load. The sample records (the four demo releases, six demo submissions, the sample split and the sample directory) are removed, and the starter data is added. Records you created yourself, such as a new artist, demo or contact, are kept. A copy of the previous data is saved in that browser under `7h-manager.data.v1.sample.<timestamp>`.
