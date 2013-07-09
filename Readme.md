
# midikeys

  A keyboard-to-midi utility module for Web Audio/Web MIDI projects.

## Installation

    $ component install nick-thompson/midikeys

## Example Usage

```javascript
var midiKeys = require('midikeys');

// A `message` event will fire on every keydown and keyup event,
// with data packaged to mimic the Web Audio API.
midiKeys.on('message', function midiMessageReceived (event) {
  var cmd = event.data[0] >> 4
    , channel = event.data[0] & 0xf
    , noteNumber = event.data[1]
    , velocity = event.data[2];

  if (cmd == 0x08) {
    myNode.start();
  } else {
    myNode.stop();
  }
});
```

## API

The object exported by MidiKeys is simply an instance of `component/emitter`.
The following documentation is from the Emitter readme.

### Emitter#on(event, fn)

  Register an `event` handler `fn`.

### Emitter#once(event, fn)

  Register a single-shot `event` handler `fn`,
  removed immediately after it is invoked the
  first time.

### Emitter#off(event, fn)

  Remove `event` handler `fn`, or pass only the `event`
  name to remove all handlers for `event`.

### Emitter#emit(event, ...)

  Emit an `event` with variable option args.

### Emitter#listeners(event)

  Return an array of callbacks, or an empty array.

### Emitter#hasListeners(event)

  Check if this emitter has `event` handlers. 

## License

  Copyright (c) 2012 Nick Thompson

  Permission is hereby granted, free of charge, to any person
  obtaining a copy of this software and associated documentation
  files (the "Software"), to deal in the Software without
  restriction, including without limitation the rights to use,
  copy, modify, merge, publish, distribute, sublicense, and/or sell
  copies of the Software, and to permit persons to whom the
  Software is furnished to do so, subject to the following
  conditions:

  The above copyright notice and this permission notice shall be
  included in all copies or substantial portions of the Software.

  THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
  EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES
  OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
  NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT
  HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY,
  WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING
  FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR
  OTHER DEALINGS IN THE SOFTWARE.
