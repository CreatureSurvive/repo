+++
title = "libCSWeather"
slug = "changelog"
+++

### Version 0.6.0b (October 22, 2018)

- Project wide refactoring and optimization 
- Proper nil condition handling
- Removed heavy @try @catch conditions
- Proper handling of iOS 11.1.2 api changes
- Added persistent backing store for caching weather data
- Fixed condition where weather would load and then return nil

---

### Version 0.5.6b (August 27, 2018)

- fix dumb mistake that may cause crashing on iOS 10 devices

---

### Version 0.5.5b (August 27, 2018)

- iOS 11 support

---

### Version 0.5.1b (January 23, 2018)

- further optimizations to fetching technique
- working on solution to verify and cache weather so it can persist through resprings without re-fetching

---

### Version 0.5.0b (January 22, 2018)

- reimplemented weather fetching technique
- added weather error reporting which logs to '/var/mobile/Documents/CSWeatherErrorLogs/'

---

### Version 0.4.9b (October 23, 2017)

- switched to a different update method when location-services are disabled
- added notification for when the current city changes
- better handling of setting the current city

---

### Version 0.4.7b (October 20, 2017)

- Added localizations for the weather condition
- Fixed a crash that could occurs if loading of data failed

---

### Version 0.4.5b (October 17, 2017)

- Added weather icon variants
- Removed F/C indicators

---

### Version 0.1.5b (October 3, 2017)

- Fixed issue causing weather information to always use the first city listed in the weather app even when Location
Services were enabled
- This will now properly check if location services are enabled and return weather info for current location
- Now offers an option to use either Celsius or Fehrenheit based off your weather app preference rather than manually
choosing Celsius or Fahrenheit

---

### Version 0.1.3b (October 1, 2017)

- initial release
