## Elements and Selected Attributes

### Page Structure

- All pages begin with `<!DOCTYPE html>` (for historical / grandfathered reasons?)
- `html`: root element
    - `lang` attribute sets page language? ex: `lang="en"`
- `head`
    - `title` element sets tab title
    - `meta` element used to set website metadata
        - `charset` attribute specifies character encoding (ex: `UTF-8`)
- `body`: for all visible content

### Visible Content (goes within `body`)

- Headings: `<h#>titletext</h#>`, where `#` in `[1, 6]`
- Paragraph: `<p>...</p>`
- Emphasis: `<em>...</em>`
- Importance/urgence: `<strong>...</strong>`

- Image: `<img src="https://src/url..." alt="displayed if image doesn't load, or for screen reader">`
- Figure: `<figure></figure>`, self-contained content.  Can have a caption.

- Hyperlink (anchor): `<a href="https://dest/url..." target="...">Link text</a>`
    - `target="_blank"` will usually open the link in a new tab (user/browser configurable, can open new window) instead of default, which is to follow the link within the current tab

- Lists:
    - Unordered: `<ul>...</ul>`
    - Ordered: `<ol>...</ol>`
    - List elements (for both kinds): `<li>...</li>`

- Content area identification (HTML5)
    - `<main>...</main>` identifies main content area
    - `<section>...</section>` identifies a distinct content section within main
    - `<footer>...</footer>` goes at the very bottom

- Comment: `<!-- Comment Text -->`

### Interactivity!  Web form

- Interactive form: `<form action="https://dest.url" name="..." placeholder="..."></form>`
    - Attributes:
        - `action` -- URL to which form data is sent
        - `name` -- allows the dest url to access data?  (**Not sure how this works yet**)
        - `required` (no value) - means it's required within the scope of current form
        - `placeholder` = prompt text

- Input element: `<input>` (self-closing, like `img`).  Goes within `form`
    - Inline element
    - Many types (selected using its `type` attribute)
        - `text` makes a word box (ENTER = submit)
        - `radio` for buttons!
            - ex: `<input type="radio"> option1`
            - When we want to make a form with multiple buttons, of which only one can be active at a time, give all of the input-radio-buttons the same `name` attribute
            - Specify lookup value using `value` attribute
        - `checkbox` for buttons for questions with more than one (or no) answer
    - Data from each input is associated with its `name`, and the data with its `value`
    - To be checked by default, use the `checked` attribute (no set value)

- Label: `<label></label>` associates text with input element itself (when clicking text, triggers input)
    - Inline
    - ex: `<label><input type="radio"> option1</label>`
    - Use like this also helps screen reader folks!
    - Can also be used just around the text, if the `for` attribute is used and set the the id of the corresponding `input` element
        - ex: `<input type="checkbox" id="x"> <label for="x">buttontext</label>`

- Fieldset: `<fieldset>...</fieldset>`, used to group related inputs/labels together within a web form
    - Blocking
- Legend: `<legend></legend>` acts as a caption for the content in the fieldset element

- Button element: `<button>...</button>`
    - Inline element
    - When no attributes are specified, default behavior is to submit the form
    - `type="submit"` to clearly indicate it's a submission button

### `id` attribute

Identifies specific HTML elements uniquely