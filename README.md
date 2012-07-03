jquery.longkeys
===============

jquery.longkeys adds two custom events to jQuery:

**longkeydown**  
**longkeypress**

These can be used to detect key strokes of specific durations.

**Note:** use of [jquery.hotkeys](https://github.com/tzuryby/jquery.hotkeys)
with this plugin is highly recommended, but not essential.

## Usage ##

In the following examples, 'keys' is a string of key identifiers, separated by periods.
Key names can be found in the
[jquery.hotkeys source](https://github.com/tzuryby/jquery.hotkeys/blob/master/jquery.hotkeys.js).

With jquery.hotkeys:

    $(element).on( 'longkeydown.keys', handler);
    $(element).off('longkeydown.keys');

With jQuery event namespacing:

    $(element).on( 'longkeydown.keys.customNameSpace', handler);
    $(element).off('longkeydown.keys.customNameSpace');

Without jquery.hotkeys:

    $(element).on( 'longkeydown.customNameSpace', handler);
    $(element).off('longkeydown.customNameSpace');

In this case the event will fire for every key, so key checking in the handler will be necessary.

## Options ##

The custom events will accept a map of options that can be used to further
customize their behavior:

**length** - the minimum length of press that is considered 'long', in milliseconds.

**onDown** - a function that will be executed when the key is first pressed,
before the length-millisecond wait.

**onShort** - a function that will be executed when the key is pressed,
but released before the required amount of time.

If **length** is omitted, it is set to 300 milliseconds by default.

Usage with options:

    $(element).on('longkeydown.keys', {
        length:  500,
        onDown:  handler1,
        onShort: handler2
    }, handler3);

