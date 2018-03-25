# Up-to-date [Web MIDI API](https://webaudio.github.io/web-midi-api/) Documentation & Resources
<img src="https://i.imgur.com/SDCmLLc.png" alt="full-mesh-midi" width="400px" />

## ⚙️ API Reference
* [MIDIAccess](./MIDIAccess.md)

## 💻 Current Web MIDI API Browser Support
The Web MIDI API is currently only supported by default in [Chromium](https://www.chromium.org/)-based browsers. It can be pulled in with a [polyfill](http://cwilso.github.io/WebMIDIAPIShim/) in some others, and is not compatible at all in a few.

### Desktop
|[Brave](https://brave.com/)|[Chrome](https://www.google.com/chrome/)|[Chrome Canary](https://www.google.com/chrome/browser/canary.html)|[Chromium](https://www.chromium.org/)|[Edge](https://www.microsoft.com/en-us/windows/microsoft-edge)|[FireFox](https://www.mozilla.org/en-US/firefox/new/)|[Internet Explorer](https://www.microsoft.com/en-us/download/internet-explorer.aspx)|[Opera](https://www.opera.com/)|[Safari](https://www.apple.com/safari/)|[Tor](https://www.torproject.org/projects/torbrowser.html)
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|✅|✅|✅|✅|🚫|🚫|🚫|✅|🚫|🚫|

### Android
|[Android](https://www.android.com/)|[Brave](https://brave.com/)|[Chrome](https://play.google.com/store/apps/details?id=com.android.chrome&hl=en)|[Edge](https://www.microsoft.com/en-us/windows/microsoft-edge-mobile)|[FireFox](https://www.mozilla.org/en-US/firefox/mobile/)|[Opera](https://www.opera.com/mobile/operabrowser)|[Samsung Internet](https://www.samsung.com/us/support/owners/app/samsung-internet)|[Tor](https://www.torproject.org/docs/android.html)|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|✅|✅|✅|🚫|🚫|✅|🚫|🚫|

### iOS
|[Chrome](https://itunes.apple.com/us/app/google-chrome/id535886823?mt=8)|[Edge](https://www.microsoft.com/en-us/windows/microsoft-edge-mobile)|[FireFox](https://itunes.apple.com/us/app/firefox-web-browser/id989804926?mt=8)|[Opera Mini](https://www.opera.com/mobile/ios)|[VPN + Tor](https://itunes.apple.com/us/app/vpn-tor-browser-private-web/id961073150?mt=8)|
|:---:|:---:|:---:|:---:|:---:|
|✅|🚫|🚫|✅|🚫|

## ✋ Current vendor positions on Web MIDI API standardization & implementation
* **Mozilla**: The [Web MIDI API RFP](https://github.com/mozilla/standards-positions/issues/58) position is still uncertain, primarily due to inherent security vulnerabilities that could be introduced by bringing [SysEx](https://en.wikipedia.org/wiki/MIDI#System_Exclusive_messages) into the web.
* **Microsoft**: After receiving [developer feedback with over 1000 votes](https://wpdev.uservoice.com/forums/257854-microsoft-edge-developer/suggestions/6508429-web-midi-api), the Web MIDI API is currently [not in the implementation roadmap](https://developer.microsoft.com/en-us/microsoft-edge/platform/status/webmidiapi/) for Microsoft Edge, Desktop, Mixed Reality, Mobile, or Xbox.
