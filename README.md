# Kiwix JS
[![Build Status](https://travis-ci.org/kiwix/kiwix-js.svg?branch=master)](https://travis-ci.org/kiwix/kiwix-js)

## Summary
Kiwix is an offline Wikipedia viewer. See the official site: http://www.kiwix.org/

This is a browser extension developed in HTML5/Javascript.

You can search among the article titles, and read any of them without any Internet access.
All the content of Wikipedia is inside your device (including the images).
It might also works with other content in the OpenZIM format: http://www.openzim.org/wiki/OpenZIM , but has been only tested on the Wikipedia ones.

If your Internet access is expensive/rare/slow/unreliable/watched/censored, you still can browse this amazing repository of knowledge and culture.

## Usage
It uses ZIM files that you can download from http://download.kiwix.org/

You have to download them separately, store them in your filesystem, and manually select them after starting the application.
It is unfortunately not technically possible to "remember" the selected ZIM file and open it automatically (the browsers refuse that for security reasons).

## Some technical details
Technically, after reading an article from a ZIM file, there is a need to "inject" the dependencies (images, css etc). For compatibility reasons, there are several ways to do it :
- the "jQuery" mode parses the DOM to find the HTML tags of these dependencies, and modifies them to put the Base64 content in it. It is compatible with any browser, but is slow and can use a lot of memory. It works well on Wikimedia content, but can miss some dependencies on some contents
- the "ServiceWorker" mode uses a Service Worker to catch any HTTP request the page would send, and reply with content read from the ZIM file. It is a generic and much cleaner way than jQuery mode, but it does not work on all browsers. And ServiceWorkers are disabled by Mozilla in Firefox extensions
- maybe a "webRequest" mode will appear, which would use the webRequest API inside the Firefox extension (when the necessary APIs will be implemented by Mozilla)

## Compatibility
This is written in HTML/javascript so it should work on many recent browser engines.

### Officially supported platforms
- Mozilla Firefox >=45 (as an extension : https://addons.mozilla.org/fr/firefox/addon/kiwix-offline/)
- Google Chrome (or Chromium) >=58 (as an extension : https://chrome.google.com/webstore/detail/kiwix/donaljnlmapmngakoipdmehbfcioahhk)
- Firefox OS >=1.2 (needs to be installed manually on the device with WebIDE)

Windows Mobile >=10 support is currently in development and is installable as a UWP application for testing via https://github.com/kiwix/kiwix-js-windows/

### Platforms that are unofficially reported to work
These platforms are not officially supported, but it has recently been reported to work on :

- Microsoft Edge
- Microsoft Internet Explorer 11

## License
This application is released under the GPL v3 license. See http://www.gnu.org/licenses/ or the included LICENSE-GPLv3.txt file
The source code can be found at https://github.com/kiwix/kiwix-js

## Unit tests
Unit tests can be run by opening tests.html file on Firefox (or Chromium/Chrome with some tweaks).

## Public releases and nightly builds
The browser extensions are distributed through the stores of each vendor (see links above). But the packages are also saved in http://download.kiwix.org/bin/browsers/ if necessary.

Some nightly builds are generated, and should only be used for testing purpose : http://download.kiwix.org/nightly/


## Previous versions
The first versions of this application were originally part of the Evopedia project: http://www.evopedia.info (now discontinued). There was a "articles nearby" feature, that was able to find articles around your location. It has been deleted from the source code with everything related to Evopedia (but still in git history in versions<=2.0.0)
These first versions were targeting Firefox OS (now discontinued too : we're not lucky ;-) ).
Some Phonegap/Cordova port was started but never finished (see in git history in versions<=2.0.0).

See the CHANGELOG.md file for the detail of previous versions.