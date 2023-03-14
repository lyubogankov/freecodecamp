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
Selectors can be combined!
    - To have multiple selectors that all get the CSS rule
        - `selector1, selector2, ... , selectorN`
    - Descendant combinators
        - `selector1 selector2` - this selects all `selector2` that are nested in `selector1`

### Properties Demonstrated

- `text-align: center`, `left`, `right`
- `background-color: brown` -> `burlywood`
    - the browser has built-in color lookup for basic colors
- `background-image: url(...)`
- `width: 300px`
    - Can be specified in...
        - pixels (`px`)
        - percentage of parent element's width (`(0, 100]%`)
- `margin-{left/right}: auto`
    - Used this to center an element within the `body`
- `padding-{left/right/top/bottom}: 20px`
    - Adds padding to the each individual side of the HTML element (between it and its parent)
- `padding: 20px`
    - Applies same padding to all 4 sides
- `display: inline-block`
    - Used this to make two blocking elements (`p`) behave as inline
    - We ended up adjusting our HTML source: the `p` elements were previously on separate lines, but were moved to be on the same line with no space between them so that we could apply `width: 50%` on both (they are `text-align`ed to `left` and `right` respectively)

### Responsiveness (to different-sized web pages)

Example from cafe menu CSS module:
- We set the menu's flavor/price text to be on the left/right side of the same inline block, each with width 50%.
- When the width of the window gets small, the text line-wraps even though there is still space.  This happens because 50% of the parent's width is now too small to fit the whole line.
- Observation: since the flavor text has more characters than the price text, we can allocate more relative width to the flavor, and the web page can go narrower before the flavor text line-wraps!