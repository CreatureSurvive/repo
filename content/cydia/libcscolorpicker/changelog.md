+++
title = "libCSColorPicker"
slug = "changelog"
+++

### Version 1.0 (April 10, 2019)

- Updated API to v1 and depreciated legacy API (Developers should update to v1 api for all new/updated projects)
- Minor refactoring of color/gradient cells
- Optimized color sliders to be more efficient and not require as many display updates
- Added more accurate brightness, saturation, and alpha slider gradient generation (the way it should have always been).
- Increased legibility of labels and elements throughout the entire color picker
- Added subtle, yet pleasing animations for all transitions
- Improved compatibility with eclipse for increased legibility
- Rewrote layout constraints, its now a lot more efficient during rotation and lighter on the layout engine
- Improved layout detection for notched devices

---

### Version 0.9.3 (April 8, 2019)

- Fixed alpha channel being ignored when copying colors, or opening the color picker
- Added `UIColor hexStringWithAlphs` instance method for convenience

---

### Version 0.9.2 (April 7, 2019)

- Fixed alpha slider being disabled by default, i forgot i designed it to be on by default

---

### Version 0.9.1 (April 7, 2019)

- Added built in Gradient Builder for building dynamic gradients in a stylish way
- Added CSGradientDisplayCell for displaying gradient previews
- Added `NSString gradientStringCGColors`, and `NSString gradientStringColors` for getting an array of UIColors, or CGColors from a gradient array string
- Fixed issue in with failsafe color in CSColorDisplayCell that could result in no color being displayed
- Fixed issue where alpha slider would always appear even when disabled

---

### Version 0.8.2 (April 1, 2019)

- Compiled with `arm64e` slice for A12 device support

---

### Version 0.8.1 (March 22, 2019)

- Fixed issue where colors would be saved to the plist using the wrong key. (caused colors to reset themselves)
- Minor refactoring

---

### Version 0.7.9 (December 31, 2018)

- Fixed bug where CSColorDisplayCell would not always update after picking a new color
- Added NSUserDefaults support, you can now fetch values instantly from NSUserDefaults

---

### Version 0.7.7 (September 8, 2018)

- Fixed issue that may prevent color preview from updating 
- Project refactoring
- Deprecated C methods

---

### Version 0.7.5 (August 17, 2018)

- Fixed issue with Eclipse altering color picker view

---

### Version 0.7.4 (August 17, 2018)

- Fixed issue with Eclipse altering color of cell previews

---

### Version 0.7.3 (July 28, 2018)

- libCSColorPicker will soon be open sourced on [GitHub](https://github.com/CreatureSurvive/libCSColorPicker)
- Added NSString convenience methods (instance & class)
- Added UIColor convenience methods (instance)
- Fixed issue where fallback would not work
- Change Refactored cell class
- Change Refactored background class
- Change Cleaned up ViewController
- Change Cleaned up slider class
- Change Added CSColorSliderType
- Change Cleaned up headers
- Change added credits where they were due (Background/UIViewParentController)

---

### Version 0.7.0 (July 27, 2018)

- Completely rewrote hex color management within the library
- Completely new public facing usage
- New format support for hex strings 'RGB', 'ARGB', 'RRGGBB', 'AARRGGBB', 'RGB:0.25', 'RRGGBB:0.25'
- Alpha slider can now be disabled using the 'alpha' specifier key
- Now supports usage with Cephei preferences by HASHBANG 
- Now uses bold system font for better legibility 
- Refactored most of the project, and improved performance

---

### Version 0.6.0 (July 22, 2018)

- Fixed layout issues on iPhone X using safe area

---

### Version 0.5.9 (October 13, 2017)

- General project cleanup
- Fixed missing depiction

---

### Version 0.5.7 (October 11, 2017)

- better support for default values
- improved layout
- better support for libCSPreferences

---

### Version 0.5.2 (April 22, 2017)

- initial release
