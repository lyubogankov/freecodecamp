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
    - Type selectors: by element name (`element`)
    - Class selectors: by class name (`.class-name`)
    - Attribute selectors: by element attribute value (`element[attr="value"]`)
    - Pseudo-selectors:
        - by element's state (`element:state`)
            -   ex: `a:visited`
        - by element's position in DOM
            - `element:last-of-type`
            - `element::after`
                - *creates* a new element that becomes the last child of selected element; we used it in cat photo gallery to push the last image from center to the left in 2-col mode (there are 9 images, so 1/3-cols are fine)
        
    - Universal selectors
        - `*` selects all elements
    
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

### Special values
- `none` sets stuff to 0
- `unset` removes earlier rules and goes back to some kind of default?

### Sizes

#### Distance
Can be expressed in...
- Pixels (`px`)
- Percentage (`%`)
    - Is it always of parent's width?
- `vh` is a special unit called **v**iewport **h**eight, and always equals 1% of the viewport's height
- `vw` is a special unit called **v**iewport **w**idth, and always equals 1% of the viewport's width

#### Angle
`+` = clockwise, `-` = counter-clockwise
- `deg`  degrees
- `turn`  1 turn = 360deg

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
- `text-transform`

Background:
- `background-color: brown` -> `burlywood`
    - the browser has built-in color lookup for basic colors
- `background-image: url(...)`
- `background: ...`

Sizing:
- `width: {width}`, can be specified in...
    - pixels (`px`) or percentage of parent element's width (`(0, 100]%`)
- `max-width: {length}`
    - Specifies an upper limit for ratio-based widths
- `min-width: {length}`

- `height: {length}`
    - Used it to change height of `hr` element
- `min-height`
- `max-height`

Position:
- `transform`
    - From MDN page: "Only transformable elements can be `transform`ed" - most CSS box model elements

- `gap`
    Shorthand for setting `row`/`column-gap` individually.  Useful for flexboxes (CSS `display: flex`), grids (CSS `display: grid`), multi-column layouts (CSS `column-count`)

Image-related:
- `filter`

    When working with images, it's easy to distort their original aspect ratio by locking or constraining width/height.

    To prevent this / preserve the aspect ratio, we can set the `object-fit` property.  A value of `cover` will maintain the aspect ratio of the image and crop it to fit within the box if needed.

Configuring display properties (blocking, inline)
- `display: {value}}`
    - `inline-block`
        - Used this to make two blocking elements (`p`) behave as inline
        - We ended up adjusting our HTML source: the `p` elements were previously on separate lines, but were moved to be on the same line with no space between them so that we could apply `width: 50%` on both (they are `text-align`ed to `left` and `right` respectively)
    - `block`
    - `flex` (CSS flexbox)

#### CSS Box Model

The "box model" of an element: `margin` is the outside, then a `border`, then `padding`, then the actual `element`
    - Margin controls space between elements/boxes (can be positive or negative)
    - Border surrounds an element, can have 0+ width
    - Padding controls space between element/its border

- [`margin`](https://developer.mozilla.org/en-US/docs/Web/CSS/margin)
    - Used this to center an element within the `body` by specifying `left/right: auto`
    - Specifies distance between it and other elements' margins
    - Can be negative!!
    - `margin-{left/right/top/bottom}: {length}`
    - `margin: {length}` (shorthand)
        - *interesting - specifying `margin: auto` doesn't center the element top/bot; it stays at the top*
    - `margin: {top/bot} {left/right}` (shorthand)
    - `margin: {top} {left/right} {bot}` (shorthand)

- `border-color: {color}`
    - default color = `black`
    - By default, each border line is 1px wide, so it adds to the shape its bordering
    - If no `border-color` is specified, I think that means the border isn't rendered (`0px`)
- `border-{left/right/top/bottom}-color: {color}`
- `border-{left/right/top/bottom}-width: {length-unit}`
- `border-{left/right/top/bottom}-style: {style}`
    - `solid`
    - `double`
- `border{-{left/right/top/bottom}}: width style color` (shorthand)
- `border: none` removes the border entirely
- `border-radius` makes rectangles have rounded corners.  Can target all, corner pairs, each corner individually

- `padding-{left/right/top/bottom}: {length-unit}`
    - Adds padding to the each individual side of the HTML element (between it and its parent)
- `padding: {length-unit}` (shorthand)
    - Applies same padding to all 4 sides
- `padding: {top&bot} {left&right}`

- [`box-shadow`](https://developer.mozilla.org/en-US/docs/Web/CSS/box-shadow)
    - `box-shadow: offsetX offsetY color`
        - `offsetX/Y` are `length-unit`s
            - `X`: positive=right, negative=left
            - `Y`: positive=down,  negative=up
    - `box-shadow: offsetX offsetY {blurRadius} {spreadRadius} color`
        - Both of the values in curly-braces are optional, see MDN docs for explanation.  I don't have a good feel for what they do yet.

- When a child does not fit inside the parent, it "overflows".  The [`overflow`](https://developer.mozilla.org/en-US/docs/Web/CSS/overflow) shorthand property (there are separate `x` and `y` properties for more fine-grained control) controls behavior.  Can be set to `visible`, `hidden`, `scroll`, or `auto` (which in FireFox does `scroll`).

- `box-sizing` controls how the CSS box model interprets element `width`/`height`.
    - By default, any padding/border added are in *addition to* the specified W/H (`box-sizing: content-box`)
    - However, setting `box-sizing: border-box` changes the behavior and border/padding *are* accounted for within the specified W/H
        - MDN's note: easier to lay out elements with `border-box` setting

#### CSS `flexbox`es

> Flexbox is a one-dimentional CSS layout that can control the way items are spaced out and aligned within a container.

To create a `flexbox`, set `display: flexbox` on an element.  This element becomes the *flex container*, and direct children are *flex items*.

Two axes:
- main: defined by `flex-direction` property

    The property values differ based on text direction of specified language: below is for L->R text direction (like English)
    - `row`: default, horizontal flex axis with items L -> R
    - `row-reverse`: horizontal R -> L
    - `column`: vertical flex axis with items T -> B
    - `column-reverse`: vertical B -> T

    The `flex-wrap` property controls how flex items behave when they overflow the flex container
    - `nowrap` (default) prevents wrapping and shrinks items to fit inside container
    - `wrap` allows wrapping to next row/col

    Positioning along main axis controlled by `justify-content` (affects space/position) (we used `center`)

- cross: the axis that is not the one specified by `flex-direction`

    `align-items` positions items along the cross axis -- its behavior varies in different scenarios, just check the [MDN docs](https://developer.mozilla.org/en-US/docs/Web/CSS/align-items)


### Responsiveness (to different-sized web pages)

Example from cafe menu CSS module:
- We set the menu's flavor/price text to be on the left/right side of the same inline block, each with width 50%.
- When the width of the window gets small, the text line-wraps even though there is still space.  This happens because 50% of the parent's width is now too small to fit the whole line.
- Observation: since the flavor text has more characters than the price text, we can allocate more relative width to the flavor, and the web page can go narrower before the flavor text line-wraps!


### Cascade

- From module "Learn the CSS Box Model by Building a Rothko Painting", we have three nested levels of `div`:
    - frame
    - canvas
    - rectangles (`one`, `two`, `three`)
    
    To make it "like a Rothko", we added `filter: blur(2px)` to the parent canvas module.  This propagated to its children, the rectangles.

    Then, the module instructed me to increase the blur radius of some of the boxes by `1px`.  I created a rule that targeted those rectangles and set `filter: blur(3px)`, but the module said this was not correct!  I changed it to `1px` and that was apparently the right answer.

    The only explanation I can think of is that the `blur` *stacks* instead of being overriden by more specific selectors??