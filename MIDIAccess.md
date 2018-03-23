# MIDIAccess
Connect your browser and [MIDI](https://en.wikipedia.org/wiki/MIDI) enabled devices with `MIDIAccess`!

## Definition
`MIDIAccess` is a [Web MIDI API](https://webaudio.github.io/web-midi-api/) interface that provides methods for listing which connected [MIDI devices](https://en.wikipedia.org/wiki/MIDI_controller) are currently available to your browser, and gives access methods for interconnecting with each device. 

The available devices are split into two categories: **inputs**, and **outputs**.

Essentially, these are the channels by which the browser can send and receive [MIDI messages](https://en.wikipedia.org/wiki/MIDI#Messages) from any external device you choose to interact with. For example: a [MIDI controller](https://en.wikipedia.org/wiki/MIDI_controller), or a [MIDI-enabled application](https://en.wikipedia.org/wiki/MIDI#Software).



## 🎉 Try it out! 🎉
<p data-height="461" data-theme-id="0" data-slug-hash="RMgLor" data-default-tab="js,result" data-user="obensource" data-embed-version="2" data-pen-title="Midi-Access-Demo" class="codepen">See the Pen <a href="https://codepen.io/obensource/pen/RMgLor/">Midi-Access-Demo</a> by Ben Michel (<a href="https://codepen.io/obensource">@obensource</a>) on <a href="https://codepen.io">CodePen</a>.</p>

**Note:** MIDI Controller Required

## 🚨 Warning! 🚨
**This is an experimental technology!** It's not quite ready for production projects yet. It is also currently only available in [Chromium](https://en.wikipedia.org/wiki/Chromium_(web_browser))-based browsers.

## Properties
`MIDIAccess` is a [`Promise`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)  object returned from an invocation of [`navigator.requestMIDIAccess`](https://webaudio.github.io/web-midi-api/#dom-navigator-requestmidiaccess).

If the promise was resolved, the [navigator interface](https://developer.mozilla.org/en-US/docs/Web/API/Navigator) returns a `MediaAccess` object containing the properties: `inputs`, `outputs`, `sysexEnabled`, and `onstatechange`.
#### .inputs
`MediaAccess.inputs` is a [MIDIInputMap](https://developer.mozilla.org/en-US/docs/Web/API/MIDIInputMap) containing the ports of all available external devices which can send MIDI messages to the `MIDIAccess` interface. This is a [Map](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map)-hybrid which is `read only`, so you cannot use common write-based map functions like `set()`, `clear()`, or `delete()` with it.
#### .outputs
`MediaAccess.outputs` is a [MIDIOutputMap](https://developer.mozilla.org/en-US/docs/Web/API/MIDIOutputMap) containing the ports of all available external devices which can receive MIDI messages from the MIDIAccess interface. This [Map](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map)-hybrid also follows the same `read only` constraints as the [`.inputs`](https://github.com/obensource/web-midi-api-docs/new/master#inputs) property.
#### .sysexEnabled
`MediaAccess.sysexEnabled` contains a `read only` boolean value that specifies if [System Exclusive](https://en.wikipedia.org/wiki/MIDI#System_Exclusive_messages) message support is permitted for a given instance of `MIDIAccess`. Enabling SysEx will introduce inherent [security risks](https://github.com/mozilla/standards-positions/issues/58#issuecomment-369892938) for you, so proceed with caution!
#### .onstatechange
`MediaAccess.onstatechange` is an event handler function that returns an [`MIDIConnectionEvent`](https://webaudio.github.io/web-midi-api/#MIDIConnectionEvent) object anytime a new MIDI port is added, or state changes for an existing port.

## Rejection Handling
In case of a rejection, you can refer the user to a great [polyfill](https://en.wikipedia.org/wiki/Polyfill_(programming)) so you’re able to use the Web MIDI API. A [MIDI-detector test](http://cwilso.github.io/WebMIDIAPIShim/) can also be used to verify if your browser currently supports it.

If it does not, you can inject this markup into your HTML source code to attain access:

`<script src='http://cwilso.github.com/WebMIDIAPIShim/build/WebMIDIAPI.min.js'></script>`

## Example Use

### Simple Access
Check to see if you browser supports the Web MIDI API, then ask the navigator for `MIDIAccess` and pass the result to your handlers (eg. `onMIDIAccess` & `onMIDIAccessFailure`).
```
if (navigator.requestMIDIAccess) {
  navigator.requestMIDIAccess({ sysex: false }).then(onMIDIAccess, onMIDIAccessFailure)
} else {
  console.warn(’This browser does not support MIDI.’)
}
```

If access has been gained, you can begin to use a `MIDIAccess` object!
```
const onMIDIAccess = (midiAccessObject)  => {
  console.log(‘The MIDI Access Object:’, midiAccessObject)
}
```

### Error Handling
Errors typically occur in two cases: there are no MIDI devices currently available, or your browser doesn’t support the Web MIDI API.

In any case, handling an error allows you to alert the user of their best available options, and log standard errors:
```
const onMIDIAccessFailure = (err) {
  console.log(`No MIDI devices are available, or the Web MIDI API isn’t supported by this browser.`)
  console.log(`Utilize this Web MIDI API Polyfill in order to use the Web MIDI API: http://cwilso.github.io/WebMIDIAPIShim/`)
  console.log(err)
}
```

### Working with raw MIDI data
By looping through the available input values from connected devices, you can pass every message to a handler and begin doing incredible things with MIDI in your browser! Have fun! 🙌
```
const onMIDIAccess = (midiAccessObject) => {
  let inputs = midiAccessObject.inputs.values()
  for (let input = inputs.next(); input && !input.done; input = inputs.next()) {
    input.value.onmidimessage = onMIDIMessage
  }  
}

const onMIDIMessage = (message) => {
  console.log(`Raw MIDI message data: ${message.data}`)
}
```

## Current Specification
[Current Web MIDI API Specification](https://webaudio.github.io/web-midi-api/). W3C Editor's Draft: November 7, 2017.
