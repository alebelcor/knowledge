# ITCSS

ITCSS stands for "**I**nverted **T**riangle architecture for **CSS**" and it's a sane, scalable, managed architecture for CSS.

It's a school of thought, not a library or framework, and it's very simple.

There are three metrics that we order stylesheets by in ITCSS:

* Generic to explicit
* Far-reaching to localized
* Low specificity to high specificity

The main idea is to use the above metrics to order and organize styles, by specificity, into "layers".

There are seven default layers in ITCSS:

1. **Settings**: Global variables, config switches, brand colors, spacing units
1. **Tools**: Default mixins and functions
1. **Generic**: Ground-zero styles, low-specificity, far-reaching (e.g. Normalize.css, resets, `box-sizing`).
1. **Base**: Unclassed HTML elements (type selectors), h1-h6, links, etc.
1. **Objects**: Cosmetic-free design patterns, agnostically named, OOCSS
1. **Components**: Designed components, chunks of UI, more explicitly named (e.g. carousels, menus)
1. **Trumps**: Helpers, overrides, utilities, only affect one piece of the DOM at a time, usually carry `!important`

"Settings" and "Tools" are only relevant if you're using preprocessors.

Need theming? Add a "Theme" layer after the Components layer.

Add layers, as needed, in the correct place. Specificity and explicitness of selectors should dictate this.

## Links

* [ITCSS @ Skillshare (video course)](https://csswizardry.com/2018/11/itcss-and-skillshare/)
* [Harry Roberts - Managing CSS Projects with ITCSS](https://www.youtube.com/watch?v=1OKZOV-iLj4)
* [Harry Roberts - Managing CSS Projects with ITCSS – Slides](https://csswizardry.net/talks/2014/11/itcss-dafed.pdf)
* [Example 1 – csswizardry.github.com](https://github.com/csswizardry/csswizardry.github.com)
* [Example 2 – inuitcss](https://github.com/inuitcss/inuitcss)
