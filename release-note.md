## 6.6.7b

### New

* You can now pause and resume downloads. Every active download has a Pause button next to Cancel. Pausing parks the downloader mid-chunk, so resuming continues instantly. Paused downloads survive an app or PC restart and pick back up at their real percentage.
* The Downloads tab is reworked: each row is a card with the progress filling its background, and one entry per game moves between Active Downloads, Download Queue, and History instead of showing up twice.
* When a source doesn't have the game, you now get a Pick Source / Cancel dialog instead of a progress bar that never moves.
* LumaCore patterns download from the new MigoReleases repository.
* Patch Gaming Mode now also enables SafeMode in SLSsteam's config, so a Steam client update disables SLSsteam instead of crashing Steam.

### Fixed

* The progress percentage now covers depot downloads only: 0% until the first depot starts, 100% when all depots are fully downloaded. It counts bytes instead of chunks and weighs each depot by its size, so the bar and the "X / Y MB" line finally agree.
* DLC luas that list base-game depots no longer crash DDMod with exit -6; each depot downloads under the app that grants access to it.
* Games whose lua filename isn't an app ID (e.g. Sledding Game) install correctly and show their real name in the Downloads tab and History.
* Corrupt manifest files (CDN error pages saved as .manifest) are rejected instead of breaking later downloads.
* A cancelled download no longer reports "Added to library" or shows up as Completed in history.
* Removing a game could corrupt SLSsteam's config.yaml by deleting unrelated lines; all config writes are now bounded to their own section.
* Installing or removing a game's Lua closes Steam first on Linux, since SLSsteam doesn't reliably reload plugins while Steam is running.
* The Gaming Mode patch backup now lands at `/usr/bin/steam-jupiter.bak`, where the docs said it would.
