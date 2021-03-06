---
layout: layout.njk
title: </> kutty - kt-swap
---

## `kt-swap`

The `kt-swap` attribute allows you to specify how the response will be swapped in relative to the
[target](/attributes/kt-target) of an AJAX request.

The possible values of this attribute are:

* `innerHTML` - The default, replace the inner html of the target element
* `outerHTML` - Replace the entire target element with the response
* `beforeBegin` - Insert the response before the target element
* `afterBegin` - Insert the response before the first child target element
* `beforeEnd` - Insert the response after the last child of target element
* `afterEnd` - Insert the response after target element

These options are based on standard DOM naming and the 
[`Element.insertAdjacentHTML`](https://developer.mozilla.org/en-US/docs/Web/API/Element/insertAdjacentHTML)
sepcification.

So in this code:

```html
  <div kt-get="/example" kt-swap="afterEnd">Get Some HTML & Append It</div>
```

The `div` will issue a request to `/example` and append the returned content after the `div`

You can modify the amount of time that kutty will wait after receiving a response to swap the content
by including a `swap` modifier:

```html
  <!-- this will wait 1s before doing the swap after it is received -->
  <div kt-get="/example" kt-swap="innerHTML swap:1s">Get Some HTML & Append It</div>
```

Similarly, you can modify the time between the swap and the settle logic by including a `settle`
modifier:

```html
  <!-- this will wait 1s before doing the swap after it is received -->
  <div kt-get="/example" kt-swap="innerHTML settle:1s">Get Some HTML & Append It</div>
```

These attributes can be used to synchronize kutty with the timing of CSS transition effects.

### Notes

* The default value of this attribute is `innerHTML`
* The default swap delay is 0ms
* The default settle delay is 100ms