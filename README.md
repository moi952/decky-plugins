# decky-plugins

Machine-readable directory of [moi952](https://github.com/moi952)'s Decky Loader
plugins — fetched at runtime (via [jsdelivr](https://www.jsdelivr.com/)) by each
plugin to show a "check out my other plugins" notification and list, without
needing a release of every other plugin whenever a new one is added here.

Consumers fetch:

```
https://cdn.jsdelivr.net/gh/moi952/decky-plugins@main/plugins.json
```

## Schema

```jsonc
{
  "schemaVersion": 1,
  "plugins": [
    {
      "id": "decky-proton-launch",       // stable slug — also the repo name.
                                          // A consuming plugin compares this
                                          // against its own id to exclude
                                          // itself from its own list/notif.
      "name": "Proton Launch",           // display name, not translated.
      "url": "https://github.com/...",   // repo page, opened on press.
      "icon": "https://cdn.jsdelivr.net/gh/.../screenshot.jpeg",
      "steamOsOnly": true,                // optional, omit if not relevant.
      "description": {                   // one short sentence per locale —
        "en-US": "...",                  // consumers fall back to en-US for
        "fr-FR": "...",                  // any locale not listed here.
        "...": "..."
      }
    }
  ]
}
```

## Updating

Adding, editing, or removing a plugin only ever means editing `plugins.json`
here and pushing — no other repo needs a new release for the change to show
up (jsdelivr's cache refreshes within ~12h; append `?<anything>` to the fetch
URL, or use jsdelivr's own purge endpoint, to force it sooner while testing).
