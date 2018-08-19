# CSS

---

## Introduction to Basic CSS

### The idea behind CSS is that you can use a selector to target an HTML element in the DOM (Document Object Model) and then apply a variety of attributes to that element to change the way it is displayed on the page.

- Attribute selector

```css
[type="radio"] {
  font-family: monospace;
}
```

- **Create & use a custom CSS Variable**

```css
--penguin-skin: gray;
background: var(--penguin-skin);
```

- **Attach a Fallback value to a CSS Variable**

```css
background: var(--penguin-skin, black);
```

- **Cascading CSS variables**
  -- By creating your variables in `:root`, they will be available throughout the whole web page.
  -- You can then over-write these variables by setting them again within a specific element.

- **Use a media query to change a variable**

```css
@media (max-width: 350px) {
  :root {
    --penguin-szie: 200px;
    --penguin-skin: black;
  }
}
```

---

## Introduction to the Applied Visual Design Challenges

### Visual Design in web development is a broad topic. It combines typography, color theory, graphics, animation, and page layout to help deliver a site's message.

- `text-align`

```css
text-align: justify | center | right | left;
```

- `box-shadow`

```css
box-shadow: offset-x offset-y ?blur-radius ?spread-radius color;
box-shadow: 0 10px 20px rgba(0, 0, 0, 0.19), 0 6px 6px rgba(0, 0, 0, 0.23);
```

- `text-transform`

```css
text-transform: lowercase | uppercase | capitalize | initial | inherit |none;
```

- `line-height`: to change the height of each line in a block of text i.e., the amount of vertical space that each line of text gets.

```css
line-height: 25px;
```

- **Pseudo-class**: A pseudo-class is a keyword that can be added to selectors, in order to select a specific state of the element.

```css
a:hover {
  color: red;
}
```

- **Relative Position**: When the position of an element is set to relative, it allows you to specify how CSS should move it relative to its current position in the normal flow of the page. Changing an element's position to relative does not remove it from the normal flow - other elements around it still behave as if that item were in its default position i.e., they hold their places.

```css
p {
  position: relative;
  bottom: 10px;
}
```

- **Absolute Positioning**: locks the element in place relative to its parent container. Unlike the relative position, this removes the element from the normal flow of the document, so surrounding items ignore it.
  _PITFALL_: One nuance with absolute positioning is that it will be locked relative to its closest positioned ancestor. If you forget to add a position rule to the parent item, (this is typically done using position: relative;), the browser will keep looking up the chain and ultimately default to the body tag.

- **Fixed Position**: a type of absolute positioning that locks an element relative to the browser window. Similar to absolute positioning, it's used with the CSS offset properties and also removes the element from the normal flow of the document. Other items no longer "realize" where it is positioned, which may require some layout adjustments elsewhere. _PITFALL_: One key difference from the absolute position is that the element won't move when the user scrolls.

```css
#navbar {
  /** Not an ideal solution in itself, because other items don't see it. So, overlaps, etc.*/
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  background-color: #767676;
}
```

- `float`: Floating elements are removed from the normal flow of a document and pushed to either the left or right of their containing parent element. It's commonly used with the width property to specify how much horizontal space the floated element requires.

```css
#left {
  float: left;
  width: 50%;
}
#right {
  float: right;
  width: 40%;
}
```

- `z-index`: When elements are positioned to overlap, the element coming later in the HTML markup will, by default, appear on the top of the other elements. However, the z-index property can specify the order of how elements are stacked on top of one another.

- **Center a block element**: Images are inline elements by default, but can be changed to block elements when you set the display property to block. Then,

```csss
margin: auto;
```

- **Colors**:

  - Complementary colors have the characteristic that if they are combined, they "cancel" each other out and create a gray color. However, when placed side-by-side, these colors appear more vibrant and produce a strong visual contrast.

  - Tertiary colors are the result of combining a primary color with one of its secondary color neighbors.

  - Different schemes:
    - split-complementary color scheme
    -

-

---

## Introduction to the Responsive Web Design Challenges

### If you expect most of your traffic to be from mobile users, take a 'mobile-first' approach. Then add conditional rules for larger screen sizes. If your visitors are desktop users, then design for larger screens with conditional rules for smaller sizes. CSS gives you the tools to write different style rules, then apply them depending on the device displaying the page.

- **Media Query**: changes the presentation of content based on different viewport sizes. The viewport is a user's visible area of a web page, and is different depending on the device used to access the site.

```css
@media (max-height: 800px) {
  p {
    font-size: 10px;
  }
}
```

- **Make an Image Responsive**: Use the following method

```css
img {
  max-width: 100%; /* scales the image to fit the width of its container, but the image won't stretch wider than its original width */
  display: block; /* changes the image from an inline element (its default), to a block element on its own line */
  height: auto; /* keeps the original aspect ratio of the image */
}
```

- **Use a Retina Image for Higher Resolution Displays**: The simplest way to make your images appear "retina" (and optimize them for retina displays) is to define their width and height values as only half of what the original file is.

```css
<style>
  img { height: 250px; width: 250px; }
</style>
<img src="coolPic500x500" alt="A most excellent picture">
```

- **Make Typography responsive**: Instead of using `em` or `px` to size text, you can use viewport units for responsive typography. Viewport units, like percentages, are relative units, but they are based off different items. Viewport units are relative to the viewport dimensions (width or height) of a device, and percentages are relative to the size of the parent container element. The four different viewport units are:
  - `vw`: `10vw` would be 10% of the viewport's width.
  - `vh`: `3vh` would be 3% of the viewport's height.
  - `vmin`: `70vmin` would be 70% of the viewport's smaller dimension (height vs. width).
  - `vmax`: `100vmax` would be 100% of the viewport's bigger dimension (height vs. width).

---

## Introduction to the CSS Flexbox Challenges

### CSS3 introduced Flexible Boxes, or flexbox, to create page layouts for a dynamic UI. It is a layout mode that arranges elements in a predictable way for different screen sizes and browsers.

- **Flex direction terms**: ![Flex direction terms](https://www.w3.org/TR/css-flexbox-1/images/flex-direction-terms.svg)

- `justify-content`: Sometimes the flex items within a flex container do not fill all the space in the container. It is common to want to tell CSS how to align and space out the flex items a certain way. Fortunately, the justify-content property has several options to do this.

```css
justify-content: flx-start | flex-end | center | space-around | space-between;
```

- `align-items`: CSS offers the `align-items` property to align flex items along the cross axis. Note that `baseline` is a text concept, think of it as the line that the letters sit on.

```css
align-items: flex-start | flex-end | center | stretch | baseline;
```

- `flex-wrap`: By default, a flex container will fit all flex items together.

```css
flex-wrap: wrap | nowrap | wrap-reverse;
```

- `flex-shrink`: Items shrink when the width of the parent container is smaller than the combined widths of all the flex items within it. For example, if one item has a `flex-shrink` value of 1 and the other has a `flex-shrink` value of 3, the one with the value of 3 will shrink three times as much as the other.

```css
flex-shrink: number;
```

- `flex-grow`: Recall that `flex-shrink` controls the size of the items when the container shrinks. The `flex-grow` property controls the size of items when the parent container expands.

```css
flex-grow: number;
```

- `flex-basis`: specifies the initial size of the item before CSS makes adjustments with `flex-shrink` or `flex-grow`. Note that the value `auto` sizes items based on the content.

```css
flex-basis: size;
```

- `flex` shorthand: The default property settings are `flex: 0 1 auto;`.

```css
flex: flex-grow flex-shrink flex-basis;
```

- `order`: tells CSS the order of how flex items appear in the flex container. By default, items will appear in the same order they come in the source HTML. The property takes numbers as values, and negative numbers can be used.

```css
order: number;
```

- `align-self`: allows you to adjust each item's alignment individually, instead of setting them all at once. It accepts the same values as `align-items` and will override any value set by the `align-items` property.

- **[Flexbox cheatsheet](http://flexbox.malven.co/)**

---

## Introduction to the CSS Grid Challenges

###

- `grid-template-columns`: You can use absolute and relative units like `px` and `em` in CSS Grid to define the size of rows and columns. You can use these as well:
  - `fr`: sets the column or row to a fraction of the available space
  - `auto`: sets the column or row to the width or height of its content automatically
  - `%`: adjusts the column or row to the percent width of its container

```css
grid-template-columns: auto 50px 10% 2fr 1fr;
```

- `grid-gap`

```css
grid-gap: grid-row-gap grid-column-gap;
```

- `justify-self`: In CSS Grid, the content of each item is located in a box which is referred to as a cell. You can align the content's position within its cell horizontally using the justify-self property on a grid item. By default, this property has a value of stretch, which will make the content fill the whole width of the cell.

```css
justify-self: start | end | center | stretch;
align-self: start | end | center | stretch;
```

- `grid-area`

```css
grid-area: horizontal line to start at / vertical line to start at / horizontal
  line to end at / vertical line to end at;
```

- `minmax`:

```css
grid-template-columns: repeat(3, minmax(90px, 1fr));
```

- `auto-fill`: This allows you to automatically insert as many rows or columns of your desired size as possible depending on the size of the container. You can create flexible layouts when combining auto-fill with minmax.

```css
grid-template-columns: repeat(auto-fill, minmax(60px, 1fr));
```

- `auto-fit`: The only difference is that when the container's size exceeds the size of all the items combined, auto-fill keeps inserting empty rows or columns and pushes your items to the side, while auto-fit collapses those empty rows or columns and stretches your items to fit the size of the container.

- **Media queries**

```css
@media (min-width: 300px) {
  .container {
    grid-template-columns: auto 1fr;
    grid-template-rows: auto 1fr auto;
    grid-template-areas:
      "advert header"
      "advert content"
      "advert footer";
  }
}
@media (min-width: 750px) {
  .container {
    grid-template-areas:
      "header header"
      "advert content"
      "footer footer";
  }
}
```

- **[CSS Grid cheatsheet](http://grid.malven.co/)**
