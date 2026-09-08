## 6.6.7c

### Fixed

* Some games use the same ID for the game itself and its only depot. SFF previously confused the two, which could prevent that game's files from being found. It now checks Steam's own records to distinguish them correctly.
* After a Native or DDMod download completed successfully, Steam would sometimes still report the game as not installed. Steam now correctly recognizes the completed install.
* An access token required by some games was being read but never actually saved. It is now saved correctly.
* For games with a large number of files, the progress bar appeared frozen while SFF checked which files were already downloaded, even though the check was still running. It now shows real-time progress during this step.
* Removed the "pin this version" prompt for older-version downloads, as it was not working reliably. Downloading a specific older version still installs exactly that version.
* The Downloads list could display the wrong source for a game if it was already queued under a different source.
