## 6.6.7c

### Fixed

* Some games use the same ID for the game and its only depot. SFF used to confuse the two, which could stop the game's files from being found. It now checks Steam's own records to tell them apart correctly.
* After downloading a game with Native or DDMod, Steam would sometimes show it as having nothing installed, even though the download finished fine. Steam now correctly sees the install.
* Some games need an extra access token saved alongside their info. This was being read but never actually saved, which could affect Steam recognizing details for those games. It's now saved properly.
* For games with a lot of files, the progress bar looked frozen while SFF checked which files were already downloaded, even though it was still working. It now shows real progress during that check.
* Removed the "pin this version" prompt when downloading an older version, since it wasn't working reliably. Downloading a specific older version still installs exactly that version.
* The Downloads list could show the wrong download source for a game if it was already queued from a different source.
