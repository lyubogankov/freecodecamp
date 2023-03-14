## CSS
**Provides styling to HTML**, override's the browser's built-in basic CSS style

Can be specified in three places:
- Within HTML source, to a specific element, using the `style` HTML attribute
- Within HTML source, within `head` -> `style`
- Outside HTML source, in a separate `.css` stylesheet document

### Basic Syntax

Comment: 
```CSS
/* ... */
```

```CSS
selector {
    property: value;
}
```
The "*selector*" *selects* which elements to apply the styling upon.
    - Type selectors: by element name (`elemen}`)
    - Class selectors: by class name (`.class-name`)
    - Pseudo-selector: by element's state (`element:state`)
        - ex: `a:visited`
Selectors can be combined!
    - To have multiple selectors that all get the CSS rule
        - `selector1, selector2, ... , selectorN`
    - Descendant combinators
        - `selector1 selector2` - this selects all `selector2` that are nested in `selector1`

### Colors

- RGB (additive): `rgb(r, g, b)` function
    - Primary colors
        - `red`  = `rgb(255, 0, 0)`
        - `blue` = `rgb(0, 0, 255)`
        - `green` color keyword != `rgb(0, 255, 0)`; = `rgb(0, 127, 0)`
    - Secondary colors (mix of two primaries at 1:1 ratio)
        - `yellow`  = `rgb(255, 255, 0)`
        - `cyan`    = `rgb(0, 255, 255)`
        - `magenta` = `rgb(255, 0, 255)`
    - Tertiary colors (mix of two primaries at 2:1 ratio)
        - `orange`       = `rgb(255, 127, 0)`
        - `springgreen`  = `rgb(0, 255, 127)`
        - `violet`       = `rgb(127, 0, 255)`
        - `chartreuse`   = `rgb(127, 255, 0)`
        - `azure`        = `rgb(0, 127, 255)`
        - `rose`         = `rgb(255, 0, 127)`
    - White: RGB all max (for 8-bit color, all `255`)
    - Black: RGB all `0`
    - .
        - ``  = `rgb()`

- CMYK (subtractive)
    - Secondary colors (combos of two primaries)
    - Tertiary colors (combos of all three primaries)

### Properties Demonstrated

- `text-align: center`, `left`, `right`
- `font-family: {font}, {fallback1}, ...`
    - ex: `sans-serif`, `serif`, `Impact`
    - Only a single font is required, but a comma-separated list will specify fallback(s) in case a particular font is not available within a browser
- `font-style: italic`
- `font-size: {size}`
    - pixels (`px`)
- `color: {color}`;
    - By default, link that has not yet been clicked is blue and visited link is purple.
    - By specifying a link color, it'll always be that color regardless of whether it has been clicked!

- `background-color: brown` -> `burlywood`
    - the browser has built-in color lookup for basic colors
- `background-image: url(...)`

- `width: {width}`, can be specified in...
    - pixels (`px`)
    - percentage of parent element's width (`(0, 100]%`)
- `max-width: {width}`
    - Specifies an upper limit for ratio-based widths

- `height: {height}`
    - Used it to change height of `hr` element

The "box model" of an element: `margin` is the outside, then a `border`, then `padding`, then the actual `element`
- `margin-{left/right/top/bottom}: {margin-size}`
    - Used this to center an element within the `body` by specifying `left/right: auto`
    - Specifies distance between it and other elements' margins
    - Can be negative!!
- `margin: {margin-size}` (shorthand property)
    - *interesting - specifying `margin: auto` doesn't center the element top/bot; it stays at the top*
- `margin: {top/bot} {left/right}` (shorthand)

- `border-color: {color}`
    - By default, each border line is 1px wide, so it adds to the shape its bordering
    - If no `border-color` is specified, I think that means the border isn't rendered (`0px`)

- `padding-{left/right/top/bottom}: 20px`
    - Adds padding to the each individual side of the HTML element (between it and its parent)
- `padding: 20px` (shorthand)
    - Applies same padding to all 4 sides
- `padding: {top&bot} {left&right}`

- `display: inline-block`
    - Used this to make two blocking elements (`p`) behave as inline
    - We ended up adjusting our HTML source: the `p` elements were previously on separate lines, but were moved to be on the same line with no space between them so that we could apply `width: 50%` on both (they are `text-align`ed to `left` and `right` respectively)
    - Can also have value `block`


### Responsiveness (to different-sized web pages)

Example from cafe menu CSS module:
- We set the menu's flavor/price text to be on the left/right side of the same inline block, each with width 50%.
- When the width of the window gets small, the text line-wraps even though there is still space.  This happens because 50% of the parent's width is now too small to fit the whole line.
- Observation: since the flavor text has more characters than the price text, we can allocate more relative width to the flavor, and the web page can go narrower before the flavor text line-wraps!