+++
title = "bubbles"
slug = "changelog"
+++

### Version 0.4.0 (April 7, 2019)

- Stable Initial stable release, officially out of beta
- Fixed Conversation Cell gradients are now smooth flowing and customizable
- Fixed Chat background images occasionaly being strangely positioned
- Fixed Typing indicator not coloring correctly
- Fixed Link Cells not being themed, (thanks u/tincan_pham for the fix)
- Fixed Typing indicator not coloring correctly
- Added Gradient color options for chat bubbles
- Added New Gradient Picker for custom gradients
- Added Support for A12 devices (arm64e)
- Updated Much more efficient gradient calculation algorithm

---

### Version 0.3.1b (March 24, 2019)

- Fixed Reaction Heart being transparent (that was tricky)
- Fixed Reaction background default colors

---

### Version 0.3.0b (August 27, 2018)

- Fixed App Drawer not hiding correctly
- Fixed disappearing cells when selecting a conversation
- Fixed adjusted contact information background blur to be darker for dark/black mode (more customization coming soon)
- Added iOS 10 support (likely has bugs, consider iOS 10 support to be in alpha)

---

### Version 0.2.9b (August 17, 2018)

- Fixed Disable App Drawer not working
- Fixed App bar color not working(temporary fix, proper fix coming tomorrow)

---

### Version 0.2.8b (August 17, 2018)

- Fixed Fixed some strange behavior with no fill bubbles coloring
- Fixed Black transition when sending a message with chat background image set
- Fixed Chat background image persisting after being disabled
- Fixed iMessage games showing as black with (borders only) turned on
- Fixed Image sending with (borders only) turned on
- Fixed Message stickers with (borders only) turned on receiving borders
- Fixed Various other issues with borders only turned on
- Fixed Add new contact view being transparent
- Fixed Optimizations to memory usage
- Fixed Optimizations to gradient colors
- Fixed Navigation bar turning white when rotating for some users
- Added Global option to disable app drawer (conflicts with noMoreAppBar)
- Added Global option to add sending progress bar to SMS (conflicts with barinProgress)
- Added Global option to disable group chat contact avatars
- Added Option to set gradient cell transparency
- Added Option to disable contact selection search bar blur
- Added Option to set contact selection search bar color
- Added Option to set Reaction selection background color

---

### Version 0.2.4b (August 14, 2018)

- Fixed some strange behavior with no fill bubbles coloring
- Fixed Chat background image scaling, proper resizing when rotating device
- Added Black (OLED) configuration
- Added Segmented Control tint color
- Added NoctisXI toggle support
- Added Option to disable navigation bar blur
- Added Initial support for Quick Reply theming
- Changed Minor tweaks to the Gradient color generation
- Changed Removed CPSUtility link
- Changed Removed SpringBoard target

---

### Version 0.2.2b (August 1, 2018)

- Fixed Conversation List background image had incorrect scale
- Fixed Light Mode failed to apply
- Fixed Light Background images setting Dark Background images
- Fixed Bubbles being filled for short messages when 'bubble borders only' option was enabled
- Added Settings changes automatically apply
- Added Experimental Gradient Bubble option (please no bug reports for this feature, its still being developed)
- Added Settings changes automatically apply
- Added Option for square chat bubbles, doesn't work with borders only option (will be expanded soon)
- Changed Internal work on iOS 10 support (Coming Soon)

---

### Version 0.2.0b (July 25, 2018)

- Fixed proper fix for Contact view by restoring blurred background
- Fixed Compose view NavigationBar title text color
- Fixed crash when using 3dTouch to set color from pasteboard
- Fixed fixed directory creation for image picker
- Added Compose view contact name color options (iMessage/SMS/default)
- Added option for background image in the chat view
- Added option for background image in the conversation list (this is experimental, and will be changing in the future)
- Added warning in preferences when restoring defaults
- Added image placeholder in backup details view

---

### Version 0.1.9b (July 24, 2018)

- [Added] option to disable blur on the input field background
- [Added] option to color input field background
- [Added] option to disable chat bubble tails
- [Added] option to customize chat footer color (below input field)
- [Added] option for bordered chat bubbles
- [Fixed] App Drawer background color not working
- [Fixed] Temporary fix for transparent Contact view (will fix background blur at another time)

---

### Version 0.1.7b (July 24, 2018)

- [Fixed] forgot to add the updated defaults in v0.1.6b, so here they are
- [Fixed] typos in new Support Page

---

### Version 0.1.6b (July 23, 2018)

- [Change] completely removed original theming method in favor of the current method
- [Change] lots of small tweaks to the default configuration
- [Change] redesigned the support page
- [Partial] started "Black Configuration"
- [Added] link color options (SMS/iMessage/Incoming)
- [Added] detail text color option for chat view
- [Added] send button color (SMS/iMessage/Incoming)
- [Added] typing dot color (typing bubble color is currently broken)
- [Added] input field text color
- [Added] input field fill color
- [Added] input field border color
- [Added] app browser background color

---

### Version 0.1.4b (July 22, 2018)

- [Fixed] Navigation Bars not coloring properly.
- [Fixed] ugly gradients on message bubbles.
- [Fixed] message bubbles disappearing.
- [Fixed] message text color being set incorrectly.
- [Fixed] lag while scrolling in chat.
- [Fixed] colors defaulting to red.
- [Fixed] default values being null.
- [Fixed] backups not being created.
- [Fixed] color picker layout on iPhone X.
- [Added] proper coloring of details view (no options yet).
- [Added] restore defaults button in backup section.
- [Change] huge improvements to performance.
- [Change] major refactoring of the project structure.
- [Change] tweaked default values.

---

### Version 0.1.0b (July 21, 2018)

- Initial Release (beta)

