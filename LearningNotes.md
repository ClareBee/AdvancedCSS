
### CSS Fundamentals
- conflicting css declarations resolved in the cascade when css is parsed
- conversion of units to pixels => stored in tree-like structure - CSSOM - css object model
- render tree = DOM and CSSOM => visual formatting model => render/paint
selector and declaration block -> declaration - property and declared value
cascade = combining stylesheets + resolving conflictsauthor (developer)/user (client)/default (browser) declarations
importance/weight - user !important, author !important, user, author, default browserspecificity - inline styles, ids, classes/pseudoclasses/attributes, elements/pseudoelements = (0, 0, 0, 0) = add them up - a single id has more specificity than a thousand classes! source order - the last is the most specific if everything else is equal NB

root font size is set in the html selector e.g. 10px? no - bad practice as prevents user overriding it (sight problems) - should be percentage of font-size provided by browser usually 16px ie.e if root font-size is 100% = 16px; 62.5% = 10pxrem = relative to this size eg 30px => 3rem =. responsive approach
css values = all converted to pixelsdeclared value - cascaded value - specified value - computed value - used value - actual value (browser/device restrictions)
em - dependent on font-size of parent element (harder to manage)
put box-sizing: inherit on global selector and box-sizing: border-box on the body
block - 100% of parent's width, line breaksinline-block - no line breaks, size of content, box-model appliesinline - size of content, only left and right margin/padding allowed, no height/width applied
positioningnormal flow eg position relativefloat - other elements will wrap around itclearfixes NBabsolute - also removes element from normal flow but other elements ignore it
stacking contexts - z-index

### CSS Architecture
- BEM, CSS architecture: block element modifier.block.block__element.block__element--modifier
- 7-1 pattern = 1 main sass file, 7 folders - base, components, layout, pages, themes, abstracts (variables/mixins), vendors 

### SASS
SASS= css preprocessor, an extensionvariables; nesting; mathematical operators; partials and imports;  mixins; functions; extends (inheritance); control directives (conditionals/loops)SASS sytax - indentation sensitive, no braces/semi-colonsSCSS syntax - preserves brackets/semicolons
@mixin mixinName($arg) {
color: $arg}@include mixinName


### Responsive Design:
- fluid grids/layouts (% rather than px); flexible/responsive images; media queries/breakpoints for viewports/devices
[class*="col-"] = containing[class^="col-"] = beginning with[class$="col-"] = ending with
define image width in % to make them responsive NBNB
media queries don't add specificity therefore code order matters
responsive images - resolution & density switching, art direction
viewport width and pixel density/resolution
use srcset and sizes
picture/source elements, media + srcset attributes

### Build Process
build process = compilation, concatenation, prefixing, compression
::selection for custom highlighting NBadd only screen to media queries - ie doesn't apply to print NB
vital to include for responsiveness =       <meta name="viewport" content="width=device-width, initial-scale=1.0">
@media only screen and (max-width: 56.25em), only screen and (hover:none)

### Flexbox
flexalign-self: stretch/flex-start etcorder: -1, 0 etcflex-growflex-basis: sets width of flex item defaults to auto, e.g. flex-basis: 20%flex-shrink - defaults to 1 - means it's allowed to shrink. if you set it to 0 it won't shrinkflex-wrap - defaults to nowrapalign-content = aligns rows-webkit-input-placeholderfill for svgs - https://css-tricks.com/almanac/properties/f/fill/scaleY(1)transform-originfill: currentColor
letter-spacing
flexbox and margin auto trick
flex: shrink grow basis;order: 1flex: 1

### CSSGrid
Gridgrid track, gutter, cellgrid gaprepeat(2, 300px), 1fr;name your gridlines NB using []grid-column: 1/21/-1 = from start to end (only works with explicit grid)cf keyword spangrid-template-columnsalign-items = aligns items in grid areasjustify-items = across row-axts/horizontallyalign-selfjustify-self
implicit and explicit gridgrid-auto-rowsgrid-auto-flow
aligning grid tracks to grid containerjustify-contentgrid-auto-flow: row dense; // fills in any holesmin-content, max-contentminmax()
name your columns (rather than your rows)

multiple background images w linear-gradient as overlayobject fit<sup>filter brightness(%)
&__seenon-text {
    display: grid;
    grid-template-columns: 1fr max-content 1fr;
    grid-column-gap: 1.5rem;
    align-items: center;

    font-size: 1.6rem;
    color: $color-grey-light-2;
// text and pseudo elements all behave like grid elements
    &::before,
    &::after {
      content: '';
      display: block;
      height: 1px;
      background-color: currentColor;
    }

set html media query to change font-size = changes value of rem


picture tag  with art-direction NBtime tag
