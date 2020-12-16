# CSS Grid

[CSS Grid](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout) is a two-dimensional grid system in CSS.

A grid is an intersecting set of horizontal (rows) and vertical lines (columns). Elements can be placed onto the grid, within these column and row lines.

To create a "grid container" use `display: grid` (or `inline-grid`). All direct children become "grid items".

Define rows and columns of a grid with the [`grid-template-columns`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-template-columns) and [`grid-template-rows`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-template-rows) properties, or the [`grid-template`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-template) shorthand. These define "grid tracks", which is the space between any two lines on the grid.

<details><summary>Example</summary>

```css
/* 4x4 grid, where each column track is 150px, and each row track is 50px */
.wrapper {
  display: grid;
  grid-template-columns: 150px 150px 150px 150px;
  grid-template-rows: 50px 50px 50px 50px;
}
```

</details>

Grid introduces the `fr` unit to help create flexible grid tracks. It represents a **fr**action of the available space.

<details><summary>Example</summary>

```css
/* 4 column grid, where all column tracks are the same size: 1/4 of the container size */
.wrapper {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr;
}
```

</details>

Use the [`repeat()`](https://developer.mozilla.org/en-US/docs/Web/CSS/repeat) function to repeat all or a section of the track listing.

<details><summary>Example</summary>

```css
/* 4 column grid, where all column tracks are the same size: 1/4 of the container size */
.wrapper {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
}

/* Same as above */
.wrapper {
  display: grid;
  grid-template-columns: 1fr repeat(1, 1fr 1fr 1fr);
}

/* Same as above */
.wrapper {
  display: grid;
  grid-template-columns: repeat(2, 1fr) 1fr 1fr;
}
```

</details>

When rows and columns are explicitly defined, with [`grid-template-columns`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-template-columns) or [`grid-template-rows`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-template-rows), the resulting grid is the "explicit grid". If you place something outside of that grid, or if the content exceeds its definition, rows and columns will be created in the "implicit grid".

Tracks on the implicit grid will be auto-sized by default based on the content inside them.

You can also define a set size for tracks for the implicit grid with the [`grid-auto-columns`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-auto-columns) and [`grid-auto-rows`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-auto-rows) properties.

<details><summary>Example</summary>

```css
/* 4 column grid, where all column tracks are the same size: 1/4 of the container size */
/* Rows in the implicit grid will be 100px tall */
.wrapper {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: 100px
}
```

</details>

Use the [`minmax()`](https://developer.mozilla.org/en-US/docs/Web/CSS/minmax) function to define a size range that considers both a minimum and a maximum size.

<details><summary>Example</summary>

```css
/* 4 column grid, where all column tracks are the same size: 1/4 of the container size */
/* Rows in the implicit grid will be at least 100px tall, while having a maximum of its content size */
.wrapper {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(100px, auto);
}
```

</details>

"Grid lines" are created when you define tracks. A 3 column, 2 row grid would produce 4 column lines and 3 row lines.

Positioning individual grid items is done targeting lines, rather than tracks, by using the [`grid-column-start`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-column-start), [`grid-column-end`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-column-end), [`grid-row-start`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-row-start) and [`grid-row-end`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-row-end) properties. There are also the shorthands [`grid-column`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-column) and [`grid-row`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-row).

<details><summary>Example</summary>

```html
<div class="wrapper">
  <div class="item1">Item 1</div>
  <div class="item2">Item 2</div>
  <div class="item3">Item 3</div>
  <div class="item4">Item 4</div>
</div>
```

```css
.wrapper {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
}

.item1 {
  grid-column-start: 1;
  grid-column-end: 3;
}

.item2 {
  grid-column-start: 3;
  grid-column-end: 4;
  grid-row-start: 1;
  grid-row-end: 3;
}
```

</details>

Negative numbers may be used as well to represent grid lines in reverse starting from the opposite side, e.g. `grid-column: 1 / -1` will span a grid item from grid line number 1 all the way to the last grid line (i.e. `-1`).

Grid lines can also be named and used, in place of the number that represents the grid line, when positioning items. Multiple names for a grid line are separated by spaces, e.g. `[sidebar-end main-start]`

<details><summary>Example</summary>

```css
.wrapper {
  display: grid;
  grid-template-columns: [start] 1fr [middle] 1fr [end];
}

.item1 {
  grid-column: start / middle;
}

.item2 {
  grid-column: middle / end;
}
```

</details>

There is also the [`span`](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout/Line-based_Placement_with_CSS_Grid#Using_the_span_keyword) keyword which, given a start or end line, specifies the number of tracks the item will take, e.g. `grid-column: 2 / span 3` will span a grid item three columns starting on grid line 2.

A "grid cell" is the smallest unit you can have on a grid. It's the space between four intersecting grid lines.

A "grid area" is one or more grid cells that make up a rectangular area on the grid. Areas are defined with the [`grid-area`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-area) property where the order of the values is: [`grid-row-start`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-row-start), [`grid-column-start`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-column-start), [`grid-row-end`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-row-end), and [`grid-column-end`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-column-end)

<details><summary>Example</summary>

```html
<div class="wrapper">
  <header class="header">Header</header>
  <aside class="sidebar">Sidebar</aside>
  <main class="main">Main</main>
  <footer class="footer">Footer</footer>
</div>
```

```css
/*
  5 column grid, where:
    - The header spans all 5 columns
    - On the next row, the sidebar spans 1 column and the main content the remaining 4 columns
    - And finally, on another row, the footer spans all 5 columns
*/
.wrapper {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
}

.header {
  grid-area: 1 / 1 / 1 / 6;
}

.sidebar {
  grid-area: 2 / 1 / 3 / 2;
}

.main {
  grid-area: 2 / 2 / 3 / 6;
}

.footer {
  grid-area: 3 / 1 / 4 / 6;
}
```

</details>

We can also define an area by giving it a name and then specify the location of that area with the [`grid-template-areas`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-template-areas) property.

<details><summary>Example</summary>

```html
<div class="wrapper">
  <header class="header">Header</header>
  <aside class="sidebar">Sidebar</aside>
  <main class="main">Main</main>
  <footer class="footer">Footer</footer>
</div>
```

```css
/*
  5 column grid, where:
    - The header spans all 5 columns
    - On the next row, the sidebar spans 1 column and the main content the remaining 4 columns
    - And finally, on another row, the footer spans all 5 columns
*/
.wrapper {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  grid-template-areas:
    'header header header header header'
    'sidebar main main main main'
    'footer footer footer footer footer';
}

.header {
  grid-area: header;
}

.sidebar {
  grid-area: sidebar;
}

.main {
  grid-area: main;
}

.footer {
  grid-area: footer;
}
```

</details>

To leave empty cells in your grid, with the above method, you can use the `.` character, e.g. `grid-template-areas: '. . header header header'`

Named areas create named lines that can be used to place items, e.g. A `sidebar` area will create named lines: `sidebar-start` and `sidebar-end`

Gutters are the spacing between grid cells. These can be created using [`grid-column-gap`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-column-gap), [`grid-row-gap`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-row-gap), or the shorthand [`grid-gap`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-gap). These properties also exist without the `grid-` prefix, but the browser support is better with the prefixed ones.

<details><summary>Example</summary>

```css
/* A 4 column grid, where there is 20px of space between columns and rows */
.wrapper {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  column-gap: 20px;
  row-gap: 20px;
}
```

</details>

A grid item can also become a grid container itself. A "nested grid" has no relationship to the parent and thus, does not inherit things, like the gutters and lines, from it.

When grid items occupy the same grid cell they overlap according to their source order but layering can also be controlled using the [`z-index`](https://developer.mozilla.org/en-US/docs/Web/CSS/z-index) property.

By default, items are placed in a grid by filling each row in turn, adding new rows as necessary. This auto-placement behavior can be modified by using the [`grid-auto-flow`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-auto-flow) property.

In grid you have two axes available to align things against:

* Block (column) axis: The axis used when laying out blocks of text
* Inline (row) axis: Runs across the block axis and is the direction along which regular text flows

The [`align-items`](https://developer.mozilla.org/en-US/docs/Web/CSS/align-items) and [`align-self`](https://developer.mozilla.org/en-US/docs/Web/CSS/align-self) properties control alignment on the block axis.

The [`justify-items`](https://developer.mozilla.org/en-US/docs/Web/CSS/justify-items) and [`justify-self`](https://developer.mozilla.org/en-US/docs/Web/CSS/justify-self) properties control alignment on the inline axis.

The [`place-items`](https://developer.mozilla.org/en-US/docs/Web/CSS/place-items) property is the shorthand for the [`align-items`](https://developer.mozilla.org/en-US/docs/Web/CSS/align-items) and [`justify-items`](https://developer.mozilla.org/en-US/docs/Web/CSS/justify-items) properties and [`place-self`](https://developer.mozilla.org/en-US/docs/Web/CSS/place-self) is the shorthand for [`align-self`](https://developer.mozilla.org/en-US/docs/Web/CSS/align-self) and [`justify-self`](https://developer.mozilla.org/en-US/docs/Web/CSS/justify-self).

If your grid tracks use an area that is smaller than the grid container, then you can align the grid tracks themselves, inside that container.

The [`align-content`](https://developer.mozilla.org/en-US/docs/Web/CSS/align-content) property controls alignment of the tracks on the block axis.

The [`justify-content`](https://developer.mozilla.org/en-US/docs/Web/CSS/justify-content) property controls alignment of the tracks on the inline axis.

The [`place-content`](https://developer.mozilla.org/en-US/docs/Web/CSS/place-content) property is the shorthand for [`align-content`](https://developer.mozilla.org/en-US/docs/Web/CSS/align-content) and [`justify-content`](https://developer.mozilla.org/en-US/docs/Web/CSS/justify-content).

Another way to align items inside their area, is to use auto margins, e.g. `margin-left: auto;`. Although this doesn't consider the writing mode, i.e. if changed from left-to-right to right-to-left.

You can target individual items and change where they appear in the UI using the [`order`](https://developer.mozilla.org/en-US/docs/Web/CSS/order) property, `grid-auto-flow: dense`, or by positioning items using line-based placement of grid template areas.

Tip: In general, avoid logical reordering of content, as it creates a mismatch between the HTML and the visual output, and thus, [accessibility issues](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout/CSS_Grid_Layout_and_Accessibility).

## Links

* [Flexbox vs. Grid (4 minute video)](https://university.webflow.com/lesson/flex-vs-grid)
* [CSS Grid Tutorial – Responsive Crash Course (43 minute video)](https://www.youtube.com/watch?v=SPFDLHNm5KQ)
* [CSS Grid (video course)](https://cssgrid.io/)
* [Introduction to CSS Grid](https://mozilladevelopers.github.io/playground/css-grid)
* [CSS Grid Layout @ MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout)
* [A Complete Guide to Grid @ CSS Tricks](https://css-tricks.com/snippets/css/complete-guide-grid/)
* [Grid Garden – A game for learning CSS Grid](https://cssgridgarden.com/)
* [GridBugs – A curated list of Grid interop issues](https://github.com/rachelandrew/gridbugs)
* [Grid @ Can I use](https://caniuse.com/#feat=css-grid)
