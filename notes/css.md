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

- RGB *Red Green Blue* (additive): `rgb(r, g, b)` function
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
    
    - Color wheel: colors placed based on similarity (hues)
        - Adjacent = hue
        - Opposite = complementary
            - combine to produce gray
            - when side-by-side, strong visual contrast + appear brighter

    - Knowledge of colors and color theory can be used to draw attention to certain site elements!

    - In CSS, colors can be specified...
        - Using keywords (ex: `red`)
        - Using `rgb()` function (ex: `rgb(255, 0, 0)`)
        - Using hexadecimal value, where each RGB channel is represented by N hex digits 
            - N = 1, 8-bit colors (ex: `#F00`)
            - N = 2, 16-bit colors (ex: `#FF0000`)
- `rgba(r, g, b, a)`
    - `a` = alpha = opacity (`[0.0, 1.0]`)
    - Can also be hexadecimal: `#RRGGBBAA`


- CMYK *?* (subtractive)

- HSL *Hue Saturation Lightness* color model: `hsl(h, s, l) function`
    - hue: [0, 360] degrees
        - red: 0deg
        - green: 120deg
        - blue: 240deg
    - saturation: [0%, 100%]
        - 0% = gray (wheel center)
        - 100% = full color (wheel circumference)
    - lightness: [0%, 100%]
        - 0% = black
        - 50% = neutral
        - 100% = white

- Can use these functions / color-setting methods to set a single color
- Can also set a gradient:
    - [`linear-gradient(gradientDirection, color1, color2 colorstopA, ...)`](https://developer.mozilla.org/en-US/docs/Web/CSS/gradient/linear-gradient)
        - creates an `image` element; typically paired with `background` property, which accepts an `image`
        - gradient direction specifies where the gradient starts, angle at which it is applied
            - default = `180deg` (top -> bot)
                - imagine a unit circle whose radius has an arrow perpendicular to it (specifies gradient direction).  At 0deg, the arrow points up, so at 180deg, the arrow points down.  Direction of rotation is CLOCKWISE, not COUNTER-clockwise like in a unit circle.
                    - 90 = left-to-right
                    - 270 = right-to-left
        - color-stops allow adjustment of gradient color placement (length unit -- `px`, `%`)
            - By default, when there are two+ colors
                - First color has stop of 0%
                - The last has stop of 100%
                - The rest are spaced evenly in between
        - *In the second CSS module, "Building a Set of Colored Markers", we used linear-gradient to make the markers look 3D cylinders (as though a light is shining on them)!*

- `opacity` property controls how much light passes through, `[0%, 100%]` or `[0.0, 1.0]`

### Sizes

#### Length
Can be expressed in...
- Pixels (`px`)
- Percentage (`%`)
    - Is it always of parent's width?

#### Height
- `vh` is a special unit called **v**iewport **h**eight, and always equals 1% of the viewport's height

#### Font Size
- `rem` = root `em` = relative to font size of HTML element
    - Used in the `margin` property??  So it can be a general unit of size, then?

### Properties Demonstrated

Text-related:
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

Background:
- `background-color: brown` -> `burlywood`
    - the browser has built-in color lookup for basic colors
- `background-image: url(...)`

Sizing:
- `width: {width}`, can be specified in...
    - pixels (`px`) or percentage of parent element's width (`(0, 100]%`)
- `max-width: {length}`
    - Specifies an upper limit for ratio-based widths

- `height: {length}`
    - Used it to change height of `hr` element

The "box model" of an element: `margin` is the outside, then a `border`, then `padding`, then the actual `element`
- `margin-{left/right/top/bottom}: {length}`
    - Used this to center an element within the `body` by specifying `left/right: auto`
    - Specifies distance between it and other elements' margins
    - Can be negative!!
- `margin: {length}` (shorthand property)
    - *interesting - specifying `margin: auto` doesn't center the element top/bot; it stays at the top*
- `margin: {top/bot} {left/right}` (shorthand)

- `border-color: {color}`
    - default color = `black`
    - By default, each border line is 1px wide, so it adds to the shape its bordering
    - If no `border-color` is specified, I think that means the border isn't rendered (`0px`)
- `border-{left/right/top/bottom}-color: {color}`
- `border-{left/right/top/bottom}-width: {length-unit}`
- `border-{left/right/top/bottom}-style: {style}`
    - `solid`
    - `double`

- `border-{left/right/top/bottom}: width style color` (shorthand)

- `padding-{left/right/top/bottom}: {length-unit}`
    - Adds padding to the each individual side of the HTML element (between it and its parent)
- `padding: {length-unit}` (shorthand)
    - Applies same padding to all 4 sides
- `padding: {top&bot} {left&right}`

- [`box-shadow`](https://developer.mozilla.org/en-US/docs/Web/CSS/box-shadow)
    - `box-shadow offsetX offsetY color`
        - `offsetX/Y` are `length-unit`s
            - `X`: positive=right, negative=left
            - `Y`: positive=down,  negative=up
    - `box-shadow: offsetX offsetY {blurRadius} {spreadRadius} color`
        - Both of the values in curly-braces are optional, see MDN docs for explanation.  I don't have a good feel for what they do yet.

Configuring display properties (blocking, inline)
- `display: {value}}`
    - `inline-block`
        - Used this to make two blocking elements (`p`) behave as inline
        - We ended up adjusting our HTML source: the `p` elements were previously on separate lines, but were moved to be on the same line with no space between them so that we could apply `width: 50%` on both (they are `text-align`ed to `left` and `right` respectively)
    - `block`


### Responsiveness (to different-sized web pages)

Example from cafe menu CSS module:
- We set the menu's flavor/price text to be on the left/right side of the same inline block, each with width 50%.
- When the width of the window gets small, the text line-wraps even though there is still space.  This happens because 50% of the parent's width is now too small to fit the whole line.
- Observation: since the flavor text has more characters than the price text, we can allocate more relative width to the flavor, and the web page can go narrower before the flavor text line-wraps!