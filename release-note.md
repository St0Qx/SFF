## 6.6.7d

### New

* A new default download source, "Free Providers". It chains the keyless providers in priority order: trionine ManifestHub, the revobd bundle (which ships real manifest files), and the ManifestHub / ManifestHub3 GitHub repos. Any manifests it finds get saved straight into depotcache, so the next download and the depot file list open instantly. This replaces MidraEveryDay, which could only supply keys.
* An Advanced link next to Depot OS opens a depot picker with checkboxes, OS and size columns, and a SteamDB link. Picking depots adds a Custom Depot OS option and downloads exactly those depots.
* Inside the depot picker, a folder icon next to each depot name opens a file explorer: the depot's full folder tree with sizes and a checkbox per entry, so you pick exactly which files download. Your selection is remembered when you reopen it, the "(N selected)" count includes every file in picked folders, and changing a selection ticks that depot automatically. Works on both engines: the native downloader filters at chunk level, DepotDownloaderMod gets a generated -filelist.
* Download sources now auto-select based on your saved keys: if you have a Hubcap key the pickers open on Hubcap, and the same for Ryuu or DepotBox. No keys means Free Providers.
* Store cards show "Updated: 3 hours ago" instead of a raw timestamp, with the exact date on hover.

### Fixed

* Opening the depot file explorer could hang forever on "Reading depot manifest...". Two causes: the result signal was never forwarded to the page, and the fetch could chain minutes of invisible retries. It now reads the local cache first and pulls provider bundles on a miss, and it tells you exactly which depot failed if one does.
* Free Providers used to "succeed" with an empty Lua when the game wasn't in the key database. It now falls through to the next provider instead.
* Saving a Hubcap key froze the window while the key was verified online. Same for the Google Drive status check; it is now capped at 2 seconds.
* Web UI changes sometimes didn't take effect after a restart because the browser engine served stale cached scripts. Local scripts and stylesheets now bypass that cache completely.
* The Depot OS default no longer offers "Auto"; it preselects your current OS so what you see is what downloads.
* The download speed meter measured decompressed bytes written, reading 2-4x your real line speed on compressed depots. It now measures what actually came off the CDN.
* DDMod exits successfully even when it never resolved a manifest, so a depot that wrote zero bytes was reported as a success. It is now marked failed, and the failing depot is named in the Downloads tab.
* Re-downloading a game right after deleting it kept showing the old "Done" row while the new download ran invisibly. A new run now takes over its old row, and failures keep their error text visible.
* If no manifest existed anywhere for a game, the download quietly finished with 0 files. It now stops with a clear "no manifest is available yet" error.
* Crack Files on Windows could report "Game install folder not found" when Steam's main folder wasn't listed in libraryfolders.vdf. The lookup now checks the Steam root.
* Version downloads reported "Complete" even when the pipeline aborted before downloading anything.
* When Steam rejects the bundled web API key, the Store list update now falls back to GitHub mirrors instead of erroring.

### Improved

* Windows downloads run the same pipeline as the Store tab: SteaMidra downloads the files itself instead of handing off to Steam, no more "add to library and press Update". LumaCore still gets the Lua so Steam accepts the install.
* The Ryuu "File type" picker is gone; the download dialog always uses the ZIP bundle.
* Downloaded manifests stay in depotcache so Steam can use them for Verify integrity and repair.
* CDN timeout warnings now log the Steam connection state, so a stale login is identifiable in debug.log instead of looking like a dead CDN.
