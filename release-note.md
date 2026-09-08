## 6.6.7c

### Fixed

* Some games use the same ID for the game itself and one of its depots. This confused depot resolution and could stop the right files from being found or downloaded.
* After a Native or DDMod download finished, Steam could still show the game's install size as 0 and prompt for an update, even though the download completed correctly.
* Access tokens listed in a game's lua weren't being saved to SLSsteam's config.yaml, even though they were read correctly.
* The Downloads tab's progress bar looked frozen while SFF checked already-downloaded files — the log kept showing "Verifying X/Y chunks" the whole time, but nothing moved on screen. It now updates in real time.
* Removed the "pin this version" prompt shown after downloading an older version, since it wasn't reliable. The correct older version still installs either way.
* The Downloads tab could show the wrong "via [source]" label for a game that was already queued from a different source.
