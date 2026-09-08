## 6.6.7c

### Fixed

* Some games use their own app ID as their only depot ID (e.g. Half-Life: Blue Shift), so ID equality alone couldn't tell a real depot from a lua's base-app marker line. Manifest resolution now checks Steam's real depot list instead of guessing.
* Native/DDMod downloads showed 0 installed depots to Steam regardless of what was actually downloaded — the ACF writer computed the depot list correctly but never wrote it in.
* `addtoken()` entries in a lua were parsed but never used; they're now written into SLSsteam's AppTokens.
* The native downloader's file-verification pass (100k+ chunks on larger depots) showed no progress at all, so the download bar looked frozen while existing files were being checked. Same for DDMod's pre-allocate/validate phases.
* The "pin this version" prompt and manifest pinning for older-version downloads have been removed. The Steam Native download path still correctly stamps the selected older build into the ACF instead of the live one.
* The Active Downloads source label could show the wrong provider if an unrelated queued entry for the same app existed.
