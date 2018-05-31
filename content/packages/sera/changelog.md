+++
title = "sera"
slug = "changelog"
+++

### Version 0.6.7 (December 26, 2016)

- Completely rewrote artwork handling, all artwork bugs are now fixed and its a lot more efficient
- Added option to swap the share/like buttons on the media controls with shuffle/repeat buttons
- Major refactor in preparation for settings redesign
- Proper bug reporting coming soon
- This update contains a lot of rewritten code, if you experience any bugs please let me know

---

### Version 0.6.1.1 (December 23, 2016)

- Fixed bug in preferences where notification positioning with media controls present would not work at all
if media controls alignment was set to top

---

### Version 0.6.1 (December 18, 2016)

- moved color pickers into alert views (temporary fix for nasty bug that reset preferences when leaving the
colorpicker)

---

### Version 0.6 (December 18, 2016)

- Added option to disable the date &amp; time section for improved compatibility with other tweaks such as
Forecast. Now you can let Forecast control the layout for the date &amp; time and still be able to adjust
the vertical position and Background height/color
- Fixed up a lot of layout bugs in blurred notification cells. I believe its bug free now, let me know if i'm
wrong

- Added ability to have multi-line date (insert an asterisk'*' in the date format where you want a new line)
- Lots of small adjustments to the preference panel
- Lots more refactoring
- I believe that sera is nearly bug free as of this release, so if you find any bugs please let me know.

---

### Version 0.5.4.2 (December 17, 2016)

- Removed apply buttons in preferences, a save button will now appear in the NavBar when editing a value.
- minor adjustments to the preferences layout

---

### Version 0.5.4 (December 17, 2016)

- Lots of refactoring
- Fixed some bugs in the normal media controls view where artwork would cover notifications, and various other
improvements

- Sera doesn’t remove ColorFlow2 background color anymore as it resulted in horrible legibility

---

### Version 0.5.3.7 (December 17, 2016)

- Fixed ColorFlow2 support (working on adding better support for compact mode right now).

---

### Version 0.5.3.6 (December 16, 2016)

- I forgot to include the fix from version 0.5.3.5 in the actual package so here it is.

---

### Version 0.5.3.5 (December 15, 2016)

- FINALLY FIXED NOTIFICATION INTERACTION BUG. a special thanks to /u/Matchstic for this fix(note: if you previously
installed LSTouch Fix(9.2+) you can remove that as its built into sera now
- A few minor adjustments to blured notification cells

---

### Version 0.5.3 (December 13, 2016)

- Fixed bug introduced in version 0.5.0.0 where album artwork wold not show up.
- Completely redesigned blurred notifications (currently there are no customization options for this.)
- Found fix for notification interaction bug, I will implement this ASAP

---

### Version 0.5.2.4 (December 10, 2016)

- Fixed some issues with notification cell blur
- Notification cell blur now compatible with Priority Hub
- If you are experiencing issues with notification interaction(cant interact with notifications) then please
install "LS Touch Fix (9.2+)" from matchstic repo "http://repo.incendo.ws/". if this fixes the issue
please let me know via the support button in settings so that I can incorporate the fix into sera.

[add source](https://cydia.saurik.com/api/share#?source=http://repo.incendo.ws)

---

### Version 0.5.2.3 (November 27, 2016)

- Fixed layout bug with Priority Hub while playing music
- Added Blurred Notification Cells(Currently Buggy with Priority Hub)

---

### Version 0.5.2.2 (November 27, 2016)

- Added support for Priority Hub (currently only supports Priority Hub set to top) you'll find a new toggle
in sera settings to enable Priority Hub support.
- Another attempt to fix notification interaction bugs(kind of shooting in the dark here since I can not reproduce
the bug on my end)

---

### Version 0.5.2.1 (November 27, 2016)

- Added option to adjust lockscreen dim delay
- Added option to prevent screen wake when receiving notifications
- Added Icons to Settings
- Yet another attempt to fix notification interaction bug affecting some users (Please anyone experiencing
this bug, send me a bug report from the support button in the settings pane. If you are still experiencing
this bug and you know how to use (FLEXing/FLEXible) please contact me if your interested in helping fix
this issue. Thank You)

---

### Version 0.5.2.0.2 (November 26, 2016)

- Fixed Creator tab not loading

---

### Version 0.5.2.0.1 (November 26, 2016)

- Moved support button to settings root for easier visibility

---

### Version 0.5.2.0 (November 26, 2016)

- NOTICE this update will alter color transparency configuration. To fix you can either need to reset sera's
settings or manually adjust the colors from within the settings
- Added Options for coloring Media Controls(Buttons, Sliders, Labels)
- Integrated libcolorpicker into settings(now depends on libcolorpicker)
- More refactoring and bug fixes

---

### Version 0.5.1.0 (November 24, 2016)

- Basic support for ColorFlow2
- Basic support for WaveFlow(not working in compact mode)
- Hopefully a fix for some users issues with notification interaction and notifications not showing

---

### Version 0.5.0.8 (November 24, 2016)

- Now has default configuration for 4", 4.7" &amp; 5.5" devices (if your using a custom resolution on your
device then the best matching configuration will be used.) Use the "reset Preferences" button to apply
defaults for your device.

---

### Version 0.5.0.7 (November 24, 2016)

- Major refactoring of the entire project, lots of optimizations
- Added option to disable blur on lockscreen
- Added option to disable tint on lockscreen
- Added option for custom tint color on lockscreen
- Added reset button in preferences to reset sera back to default settings(this should help fix a lot of configuration
issues)

- Fixed issue of Notifications not showing up(use the reset button in preferences for this to work)
- improved "Email Support" in the preferences (now attaches the users tweak list and Sera preferences to the
email to help with support on my end)

---

### Version 0.5.0.1 (November 15, 2016)

- Added options for adjusting media artwork corner radius
- Added option for adjusting media controls background height (note: this option also vertically scales the media
controls)

---

### Version 0.5.0.0 (November 15, 2016)

- Updated default configuration
- Fixed album artwork not updating when changing song
- Fixed album artwork flickering on occasion
- Added media controls compact mode toggle
- Added artwork scaling/positioning for compact mode
- Added normal mode for full size media player with customization for position

---

### Version 0.4.9.9-2 (November 14, 2016)

- Fixed Spamming of test notifications after respringing, again, whoops

---

### Version 0.4.9.9 (November 14, 2016)

- Fixed bug that would cause safe mode if an invalid hex color is entered in the settings. Now if you enter
an invalid hex color it will default to red

---

### Version 0.4.9.8 (November 14, 2016)

- Fixed album artwork appearing multiple times
- Fixed album artwork flickering when starting music from the lockscreen
- Added basic support for Xen (everything works except for Grouped Notifications)

---

### Version 0.4.9.5 (November 14, 2016)

- Added options for coloring media controls background.
- Optimization and refactoring

---

### Version 0.4.9.1 (November 14, 2016)

- Fixed spamming of test notifications after respring(forgot to remove it before release).
- Fixed some layout bugs for the notification area were it would sometimes act like media was playing when
it wasn't and cause the size to be off.
- Added proper icon

---

### Version 0.4.9 (November 13, 2016)

- Initial Beta Release
