## Learning Notes for Personal Use:
___

### CSS Fundamentals
- conflicting css declarations resolved in **cascade** when css parsed
- conversion of units to pixels => stored in tree-like structure: **CSSOM - css object model**
- render tree = DOM + CSSOM => **visual formatting model** => render/paint
- selector + declaration block (property + declared value)
- 'cascade' => combining stylesheets + resolving conflicts

#### Specificity
- importance/weight wins => user !important, author !important, user, author, default browser
- specificity: inline styles, ids, classes/pseudo-classes/attributes, elements/pseudo-elements => (0, 0, 0, 0) => add them up. See [Specificity Calculator](https://specificity.keegan.st/)
- a single id has more specificity than a thousand classes! 
- source order: the last is the most specific if everything else is equal

#### Size
- root font size set in html selector: px bad practice as prevents user overriding it (sight problems), should be percentage of font-size provided by browser usually 16px i.e. if root font-size is 100% = 16px; 62.5% = 10px
- **rem**: relative to this size eg 30px => 3rem, responsive approach

- css values => all converted to pixels
- declared value -> cascaded value -> specified value -> computed value -> used value -> actual value (browser/device restrictions)
- **em**: dependent on font-size of parent element (harder to manage)

- put `box-sizing: inherit;` on global selector and `box-sizing: border-box;` on the body

- **block**: 100% of parent's width, line breaks
- **inline-block**: no line breaks, size of content, box-model applies
- **inline**: size of content, only left and right margin/padding allowed, no height/width applied

### Positioning
See: [CSS Tricks on Position](https://css-tricks.com/almanac/properties/p/position/)
- **static**: (default) normal flow
- **relative**: normal flow but positionable in relation to this by left/right/top/bottom. doesn't affect other elements.
- **absolute**: positioned relative to its parent. also removes element from normal flow but other elements are affected and act as if it isn't there at all.
- **fixed**: removed from flow; relative to document/html; unaffected by scrolling
- **sticky**: (experimental) relative until a certain threshold then fixed
- stacking contexts - z-index doesn't work with static/undeclared position

### CSS Architecture
- BEM, CSS architecture: block element modifier: http://getbem.com/naming/
```css
.block.block__element.block__element--modifier {}
```
- **7-1 pattern** = 1 main sass file, 7 folders: base, components, layout, pages, themes, abstracts (variables/mixins), vendors: https://sass-guidelin.es/

### SASS
- SASS => css preprocessor, an 'extension'
- variables; nesting; mathematical operators; partials and imports;  mixins; functions; extends (inheritance); control directives (conditionals/loops)
- **SASS sytax** -> indentation sensitive, no braces/semi-colons
- **SCSS syntax** -> preserves brackets/semicolons
- mixins:

```scss
@mixin mixinName($arg) {
  color: $arg
}

@include mixinName
```

-  &:not(:last-child)

### Animations
- stop slight shake on animation:

```css
{
  backface-visibility: hidden;
}
```
animation-name, animation-duration, animation-iteration-count, animation-delay, animation-timing-function,

```
/* shorthand version */
animation: moveInRight 1s ease-out;
```

### Responsive Design:
- fluid grids/layouts (% rather than px); flexible/responsive images; media queries/breakpoints for viewports/devices
- define image width in % to make them responsive NB
- media queries don't add specificity therefore code order matters
- responsive images -> resolution & density switching, art direction
- viewport width (in head elements) & pixel density/resolution
- use srcset and sizes: https://html.com/attributes/img-srcset/
- picture/source elements, media + srcset attributes: https://developer.mozilla.org/en-US/docs/Web/HTML/Element/picture

### Build Process
- build process = compilation, concatenation, prefixing, compression (node-sass, postcss, autoprefixer etc.)
- https://postcss.org/

### Extras
- basic reset vs browser defaults:
```css
*,
*:after,
*:before {
  margin: 0;
  padding: 0;
  box-sizing: inherit;
}
```
- `::selection` for custom highlighting NB
- links: :link/:visited + :active/:hover: style via mixin? https://css-tricks.com/snippets/sass/sass-things-links/
- gradients

```scss
  background-image: linear-gradient(to right, $color-primary-light, $color-primary-dark);
  -webkit-background-clip: text;
  color: transparent;
```

- add `only screen` to media queries - ie doesn't apply to print NB
- vital to include for responsiveness = `<meta name="viewport" content="width=device-width, initial-scale=1.0">`
- set html media query to change font-size => changes value of rem
- [class*="col-"] = containing[class^="col-"] = beginning with, cf. [class$="col-"] = ending with
@media only screen and (max-width: 56.25em), only screen and (hover:none)
- fill for svgs - https://css-tricks.com/almanac/properties/f/fill/ `fill: currentColor`
- letter-spacing
- multiple background images w linear-gradient as overlay
- object fit: https://css-tricks.com/on-object-fit-and-object-position/
- <sup> for superscript text
- filter e.g. brightness(%), blur(), grayscale(): https://css-tricks.com/almanac/properties/f/filter/
- blend modes: https://css-tricks.com/basics-css-blend-modes/
- <time> tag: https://developer.mozilla.org/en-US/docs/Web/HTML/Element/time
- -webkit-input-placeholder

### Flexbox: https://css-tricks.com/snippets/css/a-guide-to-flexbox/
- align-self: stretch/flex-start etc
- order: -1, 0 etc
- flex-grow
- flex-basis: sets width of flex item defaults to auto, e.g. flex-basis: 20%
- flex-shrink: defaults to 1 - means it's allowed to shrink. if you set it to 0 it won't shrink
- flex-wrap: defaults to nowrap
- align-content => aligns rows: https://stackoverflow.com/questions/27539262/whats-the-difference-between-align-content-and-align-items
- flexbox and margin auto trick
- flex: shrink grow basis;
- order: 1
- flex: 1

### CSSGrid: https://css-tricks.com/snippets/css/complete-guide-grid/
- grid track, gutter, cell, grid gap
- repeat(2, 300px), 1fr;
- name your gridlines NB using []grid-column: 1/21/-1 = from start to end (only works with explicit grid)cf keyword span
- grid-template-columns
- align-items = aligns items in grid areas
- justify-items = across row-axis/horizontally
- align-self
- justify-self
- implicit and explicit grid
- grid-auto-rows
- grid-auto-flow
- aligning grid tracks to grid container
- justify-content
- grid-auto-flow: row dense; // fills in any holes
- min-content, max-content
- minmax()
- name your columns (rather than your rows)
