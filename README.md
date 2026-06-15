# TornPlus Official Repository

This repository is the official **userscript repository** for the
[Torn Plus](https://github.com/Thunderkill/TornPlusAndroid) Android app.

A userscript repository is just a hosted JSON index ([`index.json`](index.json)) that lists
userscripts and where to download them. Inside Torn Plus you can add any repository by URL
(**Settings → Userscript Manager → Browse Repositories**), browse its scripts, and install them in a
single tap. This official repository is always available in the app and cannot be removed.

> [!WARNING]
> **Install userscripts entirely at your own risk.**
> Userscripts are made by third parties and run on torn.com with access to your session — and your
> API key if the script asks for it. **Torn Plus does not create, review, endorse, or support these
> scripts and is not responsible for any damage, data loss, or action taken on your Torn account
> that they may cause.** Only install scripts you trust. No support is provided for any script,
> whether listed here or added from another repository.

## What's included

| Script | Author | Tags | What it does |
| --- | --- | --- | --- |
| [Lazy Crimes](https://greasyfork.org/scripts/540604) | Heartflower [2626587] | `crimes` `QoL` | Adds a spam crime button for Crimes. |
| [Flavourless](https://greasyfork.org/scripts/559278) | [2487979] | `crimes` `QoL` | Removes the crime flavour text. |
| [Crime Morale](https://greasyfork.org/scripts/515557) | tobytorn [1617955] | `crimes` `QoL` | A comprehensive tool for Crime 2.0. |
| [OC Role Assistant](https://github.com/Thunderkill/oc-role-assistant) | Cypher, Renger, Thunderkill | `OC` `faction` | Highlights the best OC role using configurable CPR priorities. |
| [Battle Stats Predictor](https://github.com/tdup-torn/userscripts) | TDup | `pvp` `stats` | Shows predicted battle stats from a third-party service. |

Scripts are linked here, not redistributed — the app downloads each one directly from its original
source, so updates always come from the author.

## Index format

```jsonc
{
  "name": "Repository name",          // optional, shown in the app
  "description": "Short description", // optional
  "maintainer": "Who runs it",        // optional
  "homepage": "https://...",          // optional landing page
  "formatVersion": 1,                 // optional, defaults to 1
  "scripts": [
    {
      "name": "Script name",                       // required
      "description": "What it does",               // optional
      "author": "Name [id]",                       // optional
      "version": "1.0.0",                           // optional, display only
      "downloadUrl": "https://.../script.user.js", // required — the .user.js to install
      "updateUrl": "https://.../script.meta.js",   // optional
      "homepage": "https://...",                   // optional, link to the script's page
      "tags": ["crimes", "QoL"]                    // optional categories (see Tags below)
    }
  ]
}
```

Only `scripts[].name` and `scripts[].downloadUrl` are required; everything else is display metadata.
Unknown fields are ignored, so the format can grow without breaking older app versions.

## Tags

Tags are optional **categories** the repository owner puts on a script — e.g. `crimes`, `QoL`,
`pvp`. Torn Plus shows a repository's tags as a filter bar when browsing it (and includes them in
the search box), so users can narrow a long list to a single category. Reuse the same tag across
scripts to make a real category — several `crimes` scripts collapse into one `crimes` filter.

Each tag must be **alphanumeric and 1–10 characters** (matching `^[A-Za-z0-9]{1,10}$`). The app
sanitizes tags when it loads the index — anything malformed, oversized, or duplicated (case
-insensitively) is silently dropped rather than shown — so keep them short, plain, and consistent.

```jsonc
"tags": ["crimes", "QoL"]   // on a script entry; omit the field entirely for no tags
```

## Run your own repository

Host an `index.json` like the one above anywhere reachable over HTTPS and add its URL in Torn Plus.
A public GitHub repo works out of the box — point the app at either the repo URL
(`https://github.com/owner/repo`, which resolves to `index.json` on the default branch) or a direct
raw `index.json` link.
