+++
title = "libCSPreferences"
slug = "changelog"
+++

## Version 0.9.9 (May 22, 2018)

- Added libCSPUtilities with a process manager for launching processes from anywhere.
- Added almighty tool for running processes as superuser.

---

## Version 0.9.8 (May 21, 2018)
- Refactored 3DTouch for greater compatibility

---

## Version 0.9.7 (January 22, 2018)

- added CSPCalloutCell for use of accessoryView and border callouts

---

## Version 0.9.6 (January 19, 2018)

- switched to 10.1 SDK
- added option for openInSafari to open in the safari app
- fixed interaction issue on the CSPImageCell
- initial work on verifying you are using the official liCSPreferences

---

## Version 0.9.3 (December 18, 2017)

- Added CSPreferencesAuthenticate for authenticating a package with a server
- Fixed issue where the decimal keypad would appear with a comma in some languages making it impossible to type a period
- Rewrote CSPValueCell to be more versatile

---

## Version 0.9.2 (December 11, 2017)

- Added CSPDatePickerCell just need to fix saving of the supplied date
- Added CSPValueCell for displaying a decimal value and trimming it to 4 digits

---

## Version 0.9.1 (December 11, 2017)

- Fixed bug in the preference provider that would cause colors to render incorrectly
- Added CSPVersionCell for showing the current version of the package

---

## Version 0.9.0 (December 9, 2017)

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

## Version 0.8.0 (November 28, 2017)

- cleaned up SOURCE_FILES
- fixed preferences failing to load when libCSColorPicker was not installed (even when it wasn't used by the tweak)
- added 'alsoSetKeys', and 'alsoSetKeysInverted' for applying a value to other specifiers when setting a value (keys
must be of the same value type as the specifier that is setting the values)
- added 'defaultsPath' key to the backup / restore specifier for restoring defaults from a plist

---

## Version 0.7.9 (November 7, 2017)

- added option for sub-labels on any table-cell
- added option to enable/disable any specifier when changing editing a specifier

---

## Version 0.7.8 (October 20, 2017)

- added option for isInvertedToggleGroup
- general refactoring

---

## Version 0.7.5 (October 17, 2017)

- added option to copy entire settings pages to another page
- added option to long press on a cell to copy its value to another cell(not very dynamic at the moment)

---

## Version 0.7.3 (October 13, 2017)

- initial public release
