---
title: "Element: setHTML() method"
short-title: setHTML()
slug: Web/API/Element/setHTML
page-type: web-api-instance-method
status:
  - deprecated
browser-compat: api.Element.setHTML
---

{{APIRef("HTML Sanitizer API")}}{{SecureContext_Header}}{{deprecated_header}}

The **`setHTML()`** method of the {{domxref("Element")}} interface is used to parse and sanitize a string of HTML and then insert it into the DOM as a subtree of the element.
It should be used instead of {{domxref("Element.innerHTML")}} for inserting untrusted strings of HTML into an element.

The parsing process drops any elements in the HTML string that are invalid in the context of the current element, while sanitizing removes any unsafe or otherwise unwanted elements, attributes or comments.
The default `Sanitizer()` configuration strips out XSS-relevant input by default, including {{HTMLElement("script")}} tags, custom elements, and comments.
The sanitizer configuration may be customized using {{domxref("Sanitizer.Sanitizer","Sanitizer()")}} constructor options.

## Syntax

```js-nolint
setHTML(input, options)
```

### Parameters

- `input`
  - : A string defining HTML to be sanitized.
- `options` {{optional_inline}}

  - : An options object with the following optional parameters:

    - `sanitizer`
      - : A {{domxref("Sanitizer")}} object which defines what elements of the input will be sanitized.
        If not specified, the default {{domxref("Sanitizer")}} object is used.

### Return value

None (`undefined`).

### Exceptions

None.

## Examples

The code below demonstrates how to sanitize a string of HTML and insert it into the `Element` with an id of `target`.

```js
const unsanitized_string = "abc <script>alert(1)<" + "/script> def"; // Unsanitized string of HTML
const sanitizer1 = new Sanitizer(); // Default sanitizer;

// Get the Element with id "target" and set it with the sanitized string.
document
  .getElementById("target")
  .setHTML(unsanitized_string, { sanitizer: sanitizer1 });

// Result (as a string): "abc  def"
```

> [!NOTE]
> This example uses the default sanitizer.
> The {{domxref("Sanitizer/Sanitizer","Sanitizer")}} constructor is used to configure sanitizer options.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}
