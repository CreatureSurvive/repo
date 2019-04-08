+++
title = "libCSPreferences"
slug = "changelog"
+++

### Version 1.1.1 (April 8, 2019)

- Fixed Color preview ‘copy to clipboard’ not copying the alpha channel 

---


### Version 1.1.0 (April 7, 2019)

- Added Gradient Preview support for libCSColorPicker v0.9.1 Gradient Builder
- Added Gradient Gradient array support to CSPreferencesProvider `colorsForKey` & `CGcolorsForKey`
- Fixed crash when uploading tweak list to GhostBin (Upload still fails, probably need to change providers or update the api)
- Added support for using preference icons in the navigation bar, used `icon` field from the entry specifier.

---

### Version 1.0.9 (April 1, 2019)

- Compiled with `arm64e` slice for A12 device support

---

### Version 1.0.8 (March 26, 2019)

- New Custom font loading methods, no longer injects into UIKit
- New ‘Add Font’ button in the font picker to download custom fonts from a url (You can also add font files directly to ‘/var/mobile/Documents/CSPreferences/fonts’
- New CSPDeveloperCellModern with better layout behavior

---

### Version 1.0.6 (January 1, 2019)

- Added NSUserDefaults support, saved values can now be fetched immediatly from NSUserDefaults
- Changed package compression to LZMA due to decompressing issues with meridian jailbreak

---

### Version 1.0.4 (October 22, 2018)

- Fixed crash when loading font picker
- Added localization support for cell sublabels

---

### Version 1.0.1 (September 8, 2018)

- Added GIF and Video support to image cells
- Refactored 3DTouch
- Refactored Action methods
- Refactored Respring
- Refactored tint logic
- Updated Project structure
- Finished implementing CSPDatePicker
- Reduced memory footprint
- Fixed issue with slider labels
- Updated changelog UI

---

### Version 0.9.9.9-1 (August 17, 2018)

- Fixed layout on PSSliderCell value
- Fixed CSPDateCell saving issues
- Added support for slider labels and sublabel

---

### Version 0.9.9.9 (August 4, 2018)

- Fixed issue that may cause backups not to restore
- Added callbackAction specifier key that executes after restoring defaults/backups

---

### Version 0.9.9.8 (July 29, 2018)

- Fixed Nothing new, fixes a bug affecting some users where the Settings app would crash on launch

---

### Version 0.9.9.7 (July 28, 2018)

- Fixed Refactored internal Hex Color support to resolve conflicts with other tweaks/apps
- Added Policy Alert specifier

---

### Version 0.9.9.6 (July 27, 2018)

- Rewrote colorFromHex support with new features from libCSColorPicker
- Added package piracy alert to alert users when they are using a pirated copy of a tweak and optionally disable support, or install the official repo

---

### Version 0.9.9.5 (July 25, 2018)

- Fixed crash when using 3dTouch to set color value
- Fixed set from pasteboard option appearing on color preview when no valid hex is in the clipboard
- Fixed height not being set properly when enabling/disabling cells with custom heights
- Fixed imagePickerController delegate not creating directory to save
- Fixed imageCells not saving a path value
- Added prompt to confirm when restoring defaults via the backup window
- Added placeholder image for backups on the CSPImageCell
- Fixed CSPSideImageCell not setting imageView size while laying out view
- Added Pick New Image option to CSPImagePreviewController
- Added Delete Image option to CSPImagePreviewController
- Added createDirectoryAtPath: removeLastComponent: error: to CSFileManager

---

### Version 0.9.9.4 (July 22, 2018)

- Changed to iOS 11.4 SDK.
- Added almighty.
- Added libCSPUtilities process runner.
- Fixed broken backups on iOS 11.
- Moved backup directory to 'User/Library/Preferences/CSPreferences' for persistence.

---

### Version 0.9.9.2 (May 23, 2018)

- Fixed an issue with the previous build where permissions still wouldn't be set properly for almighty.

---

### Version 0.9.9.1 (May 23, 2018)

- Fixed a permissions issue that prevented almighty from gaining root privileges.
- Looking into fixing almighty on iOS 10, just bear with me.

---

### Version 0.9.9 (May 22, 2018)

- Added libCSPUtilities with a process manager for launching processes from anywhere.
- Added almighty tool for running processes as superuser.

---

### Version 0.9.8 (May 21, 2018)
- Refactored 3DTouch for greater compatibility

---

### Version 0.9.7 (January 22, 2018)

- added CSPCalloutCell for use of accessoryView and border callouts

---

### Version 0.9.6 (January 19, 2018)

- switched to 10.1 SDK
- added option for openInSafari to open in the safari app
- fixed interaction issue on the CSPImageCell
- initial work on verifying you are using the official liCSPreferences

---

### Version 0.9.3 (December 18, 2017)

- Added CSPreferencesAuthenticate for authenticating a package with a server
- Fixed issue where the decimal keypad would appear with a comma in some languages making it impossible to type a period
- Rewrote CSPValueCell to be more versatile

---

### Version 0.9.2 (December 11, 2017)

- Added CSPDatePickerCell just need to fix saving of the supplied date
- Added CSPValueCell for displaying a decimal value and trimming it to 4 digits

---

### Version 0.9.1 (December 11, 2017)

- Fixed bug in the preference provider that would cause colors to render incorrectly
- Added CSPVersionCell for showing the current version of the package

---

### Version 0.9.0 (December 9, 2017)

- Fixed crash when 3dTouching imageCell in backup views
- Added CSPSideImageCell as a proper image selection cell with options to store selected image in a directory of
your choice
- Modified the image preview controller, will be adding UIDocumentInteractionController in the future
- Lots of improvements to the CSPMailComposeManager
- Added option to attach files with auto detected mime-types
- Added option to include logs (Cydia.log, Package.log, Condensed Package.log)
- Added device information heads including (Device Name, Device Model, and Device Software Version)
- Modified the layout of the entire project, everything is now better organized and easier to maintain. 
- Cleaned up the headers throughout the project which fixed many issues with the compilation process
- Added proper restring support with option to either respring with a nice fade out animation or restring and return
to the settings page
- Added ‘isDecimalWithNegetive’ keyboard option to PSEditTextCell specifiers which adds a keyboard toolbar with an
option to toggle negative/positive on the DecimalKeypad
- Refactored all the alert views for copying tweak lists and resprings
- Added alpha, red, green, blue, hue, saturation, and brightness convenience methods to UIColor+ColorFromHex 
- Fixed compilation error with with the CSPBackupItemView (that was annoying)
- Added Preview for CSPSideImageCell
- Added CSPProcessManager for running commands via NSTask rather than ugly posix_spawn or depreciated system()

---

### Version 0.8.0 (November 28, 2017)

- cleaned up SOURCE_FILES
- fixed preferences failing to load when libCSColorPicker was not installed (even when it wasn't used by the tweak)
- added 'alsoSetKeys', and 'alsoSetKeysInverted' for applying a value to other specifiers when setting a value (keys
must be of the same value type as the specifier that is setting the values)
- added 'defaultsPath' key to the backup / restore specifier for restoring defaults from a plist

---

### Version 0.7.9 (November 7, 2017)

- added option for sub-labels on any table-cell
- added option to enable/disable any specifier when changing editing a specifier

---

### Version 0.7.8 (October 20, 2017)

- added option for isInvertedToggleGroup
- general refactoring

---

### Version 0.7.5 (October 17, 2017)

- added option to copy entire settings pages to another page
- added option to long press on a cell to copy its value to another cell(not very dynamic at the moment)

---

### Version 0.7.3 (October 13, 2017)

- initial public release
