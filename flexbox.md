# Flexbox

Flexbox was designed as a [one-dimensional layout model](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout/Relationship_of_Flexbox_to_Other_Layout_Methods), i.e. rows or columns.

Think in terms of two axes: main axis and cross axis

Main axis is defined by the [`flex-direction`](https://developer.mozilla.org/en-US/docs/Web/CSS/flex-direction) property. The cross axis runs perpendicular to it.

[`flex-direction`](https://developer.mozilla.org/en-US/docs/Web/CSS/flex-direction) has four possible values:

* `row`: items are laid out in a line
* `row-reverse`: like `row`, but reversed
* `column`: items are laid out in a column
* `column-reverse`: like `column`, but reversed

To create a "flex container" use `display: flex` (or `inline-flex`). All immediate children will be "flex items".

By default flex items will display in a row, from the start edge of the main axis, they will not stretch but will shrink, and won't wrap into multiple lines.

Set [`flex-wrap`](https://developer.mozilla.org/en-US/docs/Web/CSS/flex-wrap) to `wrap`, on the flex container, to cause flex items to wrap into multiple lines.

[`flex-flow`](https://developer.mozilla.org/en-US/docs/Web/CSS/flex-flow) is a shorthand for [`flex-direction`](https://developer.mozilla.org/en-US/docs/Web/CSS/flex-direction) and [`flex-wrap`](https://developer.mozilla.org/en-US/docs/Web/CSS/flex-wrap).

To have more control over flex items we use:

* [`flex-grow`](https://developer.mozilla.org/en-US/docs/Web/CSS/flex-grow): the flex grow factor of a flex item
* [`flex-shrink`](https://developer.mozilla.org/en-US/docs/Web/CSS/flex-shrink): the flex shrink factor of a flex item
* [`flex-basis`](https://developer.mozilla.org/en-US/docs/Web/CSS/flex-basis): the value the item is using as their base value to grow and shrink from

`flex-basis: auto` makes it so items will use either their explicit width, or the (implicit) width of their content.

Giving [`flex-grow`](https://developer.mozilla.org/en-US/docs/Web/CSS/flex-grow) a positive value means the item can grow.

`flex-grow: 0;` makes it so items will not grow larger than their [`flex-basis`](https://developer.mozilla.org/en-US/docs/Web/CSS/flex-basis) size.

Giving [`flex-shrink`](https://developer.mozilla.org/en-US/docs/Web/CSS/flex-shrink) a positive value the items can shrink smaller than their [`flex-basis`](https://developer.mozilla.org/en-US/docs/Web/CSS/flex-basis), but only if their total values overflow the main axis.

`flex-shrink: 1` makes it so items can shrink if they need to rather than overflowing.

The [`flex`](https://developer.mozilla.org/en-US/docs/Web/CSS/flex) shorthand sets [`flex-grow`](https://developer.mozilla.org/en-US/docs/Web/CSS/flex-grow), [`flex-shrink`](https://developer.mozilla.org/en-US/docs/Web/CSS/flex-shrink), and [`flex-basis`](https://developer.mozilla.org/en-US/docs/Web/CSS/flex-basis) in that order.

`flex: initial` is the default for flex items, and the same as `flex: 0 1 auto`.

`flex: auto` is equivalent to `flex: 1 1 auto`.

`flex: none` is equivalent to `flex: 0 0 auto`.

`flex: 1` is equivalent to `flex: 1 1 0`.

Tip: Specify all the values to the [`flex`](https://developer.mozilla.org/en-US/docs/Web/CSS/flex) shorthand to avoid confusion and bugs.

[`justify-content`](https://developer.mozilla.org/en-US/docs/Web/CSS/justify-content) controls alignment of items on the main axis. Initial value is `flex-start`

[`align-items`](https://developer.mozilla.org/en-US/docs/Web/CSS/align-items) controls alignment of items on the cross axis. Initial value is `stretch`.

[`align-content`](https://developer.mozilla.org/en-US/docs/Web/CSS/align-content) controls space between flex lines (i.e. when wrapped) on the cross axis.

[`align-self`](https://developer.mozilla.org/en-US/docs/Web/CSS/align-self) controls alignment of an individual flex item on the cross axis.

There are no individual alignment properties (e.g. `justify-items` or `justify-self`) on the main axis as those items are treated as a group. However, it is possible to do individual alignment using [auto margins](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout/Aligning_Items_in_a_Flex_Container#Using_auto_margins_for_main_axis_alignment) (e.g. `margin-left: auto`).

You can target individual items and change where they appear in the UI with the [`order`](https://developer.mozilla.org/en-US/docs/Web/CSS/order) property.

Items are assigned an integer that represents their group. The items are then placed in the visual order according to that integer, lowest values first. If more than one item has the same integer value, then within that group the items are laid out as per source order.

Negative values are accepted. Flex items have a default [`order`](https://developer.mozilla.org/en-US/docs/Web/CSS/order) value of `0`.

Tip: In general, avoid `-reverse` values in `flex-direction`/`flex-flow`, and using the [`order`](https://developer.mozilla.org/en-US/docs/Web/CSS/order) property as they create a mismatch between the HTML and the visual output, and thus, [accessibility issues](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout/Ordering_Flex_Items).

## Links

* [Flexbox vs. Grid (4 minute video)](https://university.webflow.com/lesson/flex-vs-grid)
* [What The Flexbox?! (video course)](https://flexbox.io/)
* [CSS Flexible Box Layout @ MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout)
* [A Complete Guide to Flexbox @ CSS Tricks](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
* [Flexbox Froggy – A game for learning CSS Flexbox](https://flexboxfroggy.com/)
* [Flexbugs – A community-curated list of Flexbox issues and cross-browser workarounds for them](https://github.com/philipwalton/flexbugs)
* [Flexbox @ Can I use](https://caniuse.com/#feat=flexbox)
