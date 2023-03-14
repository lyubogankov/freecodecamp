## Elements and Selected Attributes

### Page Structure

- All pages begin with `<!DOCTYPE html>` (for historical / grandfathered reasons?)
- `html`: root element
    - `lang` attribute sets page language? ex: `lang="en"`
- `head`
    - `title` element sets tab title
    - `meta` element used to set website metadata - recommendation is one element per attribute
        - `charset` attribute specifies character encoding (ex: `UTF-8`)
        - self-closing
    - `link`
        - `rel="stylesheet"` + `href="..."` to specify which stylesheet to use
        - self-closing
    - > For the styling of the page to look similar on mobile as it does ona desktop or laptop, you need to add a `meta` element with a special `content` attribute.
        - `<meta name="viewport" content="width=device-width, initial-scale=1.0" />`
            - This apparently makes the webpage "look the same on all devices"
- `body`: for all visible content

### Visible Content (goes within `body`)

- Headings: `<h#>titletext</h#>`, where `#` in `[1, 6]`
- Paragraph: `<p>...</p>`
- Emphasis: `<em>...</em>`
- Importance/urgence: `<strong>...</strong>`

- Image: `<img src="https://src/url..." alt="displayed if image doesn't load, or for screen reader">`
    - > "like" inline elements
- Figure: `<figure></figure>`, self-contained content.  Can have a caption.

- Hyperlink (anchor): `<a href="https://dest/url..." target="...">Link text</a>`
    - `target="_blank"` will usually open the link in a new tab (user/browser configurable, can open new window) instead of default, which is to follow the link within the current tab
    - States (addressable by CSS psuedo-selector):
        - `visited` (already clicked)
        - `hover` (mouse currently hovering)
        - `active` (mouse currently clicking on the link)

- Lists:
    - Unordered: `<ul>...</ul>`
    - Ordered: `<ol>...</ol>`
    - List elements (for both kinds): `<li>...</li>`

- Content area identification (HTML5)
    - `<main>...</main>` identifies main content area
    - `<section>...</section>` identifies a distinct content section within main
    - `<article>...</article>` "commonly contains multiple elements that have related information"
        - Within freecodecamp cafe menu example, we used this element to group two `p` elements (one for menu item, the other for its price)
    - `<footer>...</footer>` goes at the very bottom

- Comment: `<!-- Comment Text -->`

- Horizontal rule: `hr` (adds a horizontal line)
    - Self-closing


### Special attributes

- `id` identifies specific HTML elements uniquely
- `class` can be used to group elements; more than one class can be applied to an element!
    - `class="class1 class2 ..."`

### Non-semantic wrappers
Do not have a specific semantic meaning.  If no other elements fit, use these.  Can be targeted with CSS (they are often used to group other elements)
- `div`: blocking
- `span`: inline


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