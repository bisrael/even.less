# even.less
## A LESS CSS library with one goal: write.even.less.

even.less is a library for LESS CSS that utilizes extremely terse naming abbreviations
coupled with consistency to make write you LESS files faster, easier and smaller.

## API
### Box Model
#### Display

- `.dsp(@value)` --> set `display: @value`
- `.none()` --> `none`
- `.blk()` --> `block`
- `.nln()` --> `inline`
- `.iblk()` --> `inline-block`

#### Position

- `.pos(@value)` --> set `position: @value`
- `.rel()` --> `relative`
- `.abs()` --> `absolute`
- `.fxd()` --> `fixed`
- `.stc()` --> `static`

#### Offsets (top/left/right/bottom)

- `.l(@value)` --> `left: @value`
- `.r(@value)` --> `right: @value`
- `.t(@value)` --> `top: @value`
- `.btm(@value)` --> `bottom: @value` (`.b` is used by `border`, a far more common property)

There are several compound offset properties, the second param is always optional and, if omitted, will be the same as the first:

- `.tl(@top[, @left])` --> top & left
- `.tr(@top[, @right])` --> top & right
- `.btml(@btm[, @left])` --> bottom & left
- `.btmr(@btm[, @right])` --> bottom & right

Note: Compound properties for top & bottom, or left & right don't exist because of their basically pointless use in
most every day settings.

Additionally, the following utility function exists for quickly setting something to absolute position with an x and y:

- `.xy(@x[, @y])` --> absolute, left, & top

#### Margins

Margin mixins use the `.m` prefix, plus optional `t, l, b, r` suffixes for combination methods (top, left, bottom, and right, respectively)

- `.m(@value)` --> `margin: @value`
- `.mt(@value)` --> `margin-top`
- `.ml(@value)` --> `margin-left`
- `.mb(@value)` --> `margin-bottom`
- `.mr(@value)` --> `margin-right`

Combinations (currently only two-sided combos exist, three-sided do not):

- `.mtl(@top[, @left])` --> top & left
- `.mtr(@top[, @right])` --> top & right
- `.mbl(@btm[, @left])` --> bottom & left
- `.mbr(@btm[, @right])` --> bottom & right
- `.mtb(@top[, @btm])` --> top & bottom
- `.mlr(@left[, @right])` --> left & right

#### Padding

Padding mixins follow the same rules as the margin mixins, but use the `.p` prefix

- `.p(@value)` --> `padding: @value`
- `.pt(@value)` --> `padding-top`
- `.pl(@value)` --> `padding-left`
- `.pb(@value)` --> `padding-bottom`
- `.pr(@value)` --> `padding-right`

Combinations:

- `.ptl(@top[, @left])` --> top & left
- `.ptr(@top[, @right])` --> top & right
- `.pbl(@btm[, @left])` --> bottom & left
- `.pbr(@btm[, @right])` --> bottom & right
- `.ptb(@top[, @btm])` --> top & bottom
- `.plr(@left[, @right])` --> left & right

#### Borders

Since Borders are much more complex than Margins or Padding, they occupy several prefixes:

- `.b(@width, @color[, @style: solid])` --> `border: @width @style @color`
  - `.bt(@width, @color[, @style: solid])` --> `border-top`
  - `.bl(@width, @color[, @style: solid])` --> `border-left`
  - `.bb(@width, @color[, @style: solid])` --> `border-bottom`
  - `.br(@width, @color[, @style: solid])` --> `border-right`
  - Because of the number of parameters and the use of defaults, mutli-side combination mixins only take one set of params and use it for both sides
    - `.btl(@width, @color[, @style: solid])` --> top & left
    - `.btr(@width, @color[, @style: solid])` --> top & right
    - `.bbl(@width, @color[, @style: solid])` --> bottom & left
    - `.bbr(@width, @color[, @style: solid])` --> bottom & right
    - `.btb(@width, @color[, @style: solid])` --> top & bottom
    - `.blr(@width, @color[, @style: solid])` --> left & right
- `.bw(@value)` --> `border-width: @value`
  - `.bwt(@value)` --> top
  - `.bwl(@value)` --> left
  - `.bwb(@value)` --> bottom
  - `.bwr(@value)` --> right
- `.bc(@value)` --> `border-color: @value`
- `.bs(@value)` --> `border-style: @value`
- `.brd(@value)` --> `border-radius: @value`
  - (Note: `.brd` and it's combos set vendor-prefixed properties like `-webkit-border-radius`)
  - `.brd` combos work a bit differently: single corner settings use two letters like `.brdtr` for setting the top-right border-radius.
  - However, one letter suffixes like `.brdt` set _both_ top corners (top-left & top-right)

### Decorations
#### Basics

- `.c(@color)` --> `color: @color`

#### Backgrounds

- `.bg(@value)` --> `background: @value`
- `.bgc(@color)` --> `background-color: @color`
- `.bgi(@image)` --> `background-image: @image`

Additional Background Settings:

- `.bgr(@value)` --> `background-repeat: @value`
  - `.bgr-no()` --> `no-repeat`
  - `.bgr-x()` --> `repeat-x`
  - `.bgr-y()` --> `repeat-y`

### CSS3 Transformations & Transitions

#### Transitions

- `.xtn(@value)` --> `transition: @value` & vendor-prefixes
- `.xtn(@time, @function[, @property: all])` --> useful for applying an all transition

#### Transforms

- `.xfm(@value)` --> `transform: @value` & vendor-prefixes
- `.rot(@angle)` --> rotate by angle
- `.scl(@factor)` --> scale by factor
- `.skw(@x-angle, @y-angle)` --> skew by x-angle and y-angle
- `.xlt(@x, @y)` --> translate by x,y

Since CSS Transforms will override each other with successive property declarations, we need combos.
Combos are chained in alphabetical order (by abbreviation, not function-name).

- `.rot-scl(@angle, @factor)`
- `.rot-skw(@angle, @x-angle, @y-angle)`
- `.rot-xlt(@angle, @x, @y)`
