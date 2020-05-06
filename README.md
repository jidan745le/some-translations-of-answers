# some-translations-of-answers
##1.about structured-clonable-type
Actually found the answer right away, it's in the docs. You basically can't have a Function-type property (which probably is there somewhere inside the io() object) because it can't be cloned:

Parameters
message The message to send to the service worker. This can be any structured-clonable type.

A structured-clonable-type being defined as:

The structured clone algorithm is an algorithm defined by the HTML5 specification for copying complex JavaScript objects. It is used internally when transferring data to and from Workers via postMessage(). It builds up a clone by recursing through the input object while maintaining a map of previously visited references in order to avoid infinitely traversing cycles.

Things that don't work with structured clone

Error and Function objects cannot be duplicated by the structured clone algorithm; attempting to do so will throw a DATA_CLONE_ERR exception. Attempting to clone DOM nodes will likewise throw a DATA_CLONE_ERR exception. Certain parameters of objects are not preserved: The lastIndex field of RegExp objects is not preserved. Property descriptors, setters, and getters (as well as similar metadata-like features) are not duplicated. For example, if an object is marked read-only using a property descriptor, it will be read-write in the duplicate, since that's the default condition. The prototype chain does not get walked and duplicated.
