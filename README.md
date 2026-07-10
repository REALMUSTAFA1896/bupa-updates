# bupa-updates

Central **update + news hub** for BUPA scripts. Every script pulls its version
and marketing info from this repo. Must be **public**.

## Structure

```
bupa-updates/
├── news.txt            # shared marketing text shown in every server console
├── bupa-animpos.json   # bupa-animpos version + changelog + download link
└── (new script)        # add one .json per new script: bupa-garage.json ...
```

## Script version file format (`<script-name>.json`)

```json
{
  "version": "1.5.0",
  "download": "https://portal.cfx.re/assets/granted-assets?search=bupa-animpos",
  "changelog": [
    "First line",
    "Second line"
  ]
}
```

| Field | Description |
| --- | --- |
| `version` | Latest version of the script. If higher than the script's `fxmanifest.lua` `version`, the customer sees "UPDATE AVAILABLE". |
| `download` | Download link shown in the console (Cfx.re portal / Tebex). |
| `changelog` | Listed line by line under "What's new" (array). |

## When you release a new version

1. Bump the script's `fxmanifest.lua` `version` (e.g. `1.6.0`).
2. Set the same number in this repo's `<script>.json` `version` and update `changelog`.
3. `git push`. Every server running an older version sees the notice in console.

## When you add a new script

Set `UPDATES.Script` in the new script's `server.lua` to its file name
(e.g. `bupa-garage`) and add `bupa-garage.json` to this repo. All scripts feed from
the same hub.
