# Web Performance

## Web Fonts

### Formats

Use <abbr title="Web Open Font Format">WOFF</abbr> 2.0 or 1. They have the widest browser support and yield the smallest file size than other formats.

If you don't need to support IE 11, [use WOFF 2.0](https://caniuse.com/woff2):

```css
/* assumes a regular (i.e. 400) normal (i.e. non-italic) font */
@font-face {
    font-family: 'Font Name';
    font-style: normal;
    font-weight: 400;
    src: url('/path/to/file.woff2') format('woff2');
}
```

If you need to support IE 11, add [WOFF 1](https://caniuse.com/woff) for it:

```css
/* assumes a regular (i.e. 400) normal (i.e. non-italic) font */
@font-face {
    font-family: 'Font Name';
    font-style: normal;
    font-weight: 400;
    src: url('/path/to/file.woff2') format('woff2'),
         url('/path/to/file.woff') format('woff');
}
```

### font-display

The [`font-display`](https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face/font-display) descriptor lets you control what happens while the font is still loading or otherwise unavailable.

Use the `swap` value [to ensure text remains visible during font loading and avoid a flash of invisible text (FOIT)](https://web.dev/font-display/).

Use the `optional` value when the font is non-essential to the design. It will optionally load the font on fast enough connections.

### Preloading

[Preload](https://developer.mozilla.org/en-US/docs/Web/HTML/Preloading_content) fonts to increase the likelihood of them being loaded when your document is first rendered, thus avoiding a layout shift:

```html
<head>
  <link rel="preload" href="/path/to/file.woff2" as="font" type="font/woff2" crossorigin>
</head>
```

### Character ranges

Use the [`unicode-range`](https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face/unicode-range) descriptor to define one, or more, specific ranges of characters to be used from a font defined by `@font-face`. If the page doesn't use any character in the range, the font is not downloaded; if it uses at least one, the whole font is downloaded.

Google Fonts outputs different ranges using `unicode-range`: [Example](https://fonts.googleapis.com/css2?family=Roboto&display=swap)

### Subsetting

Subsetting allows you to include only the characters/glyphs you want instead of a full font file.

For example, subsetting to basic latin characters for an English only site.

### Misc

Use long [HTTP caching](https://web.dev/http-cache/#cache-control) for fonts, since they are static resources that don't see frequent updates.

Avoid using the Google Fonts service and [self-host the fonts instead](https://wicki.io/posts/2020-11-goodbye-google-fonts/).

Avoid using the `local()` function, in `@font-face`, to prevent showing potentially unexpected locally installed fonts.

Consider using [variable fonts](https://web.dev/variable-fonts/) ([browser support](https://caniuse.com/variable-fonts)).

## Links

* [google-webfonts-helper (Online) – Get (Google Fonts) eot, ttf, svg, woff and woff2 files + CSS snippets](https://github.com/majodev/google-webfonts-helper)
* [fontTools (CLI) – a library for manipulating fonts](https://github.com/fonttools/fonttools)
* [Font Squirrel (Online) – Create Your Own @font-face Kits](http://www.fontsquirrel.com/tools/webfont-generator)
* [glyphhanger (CLI) – Your web font utility belt](https://github.com/filamentgroup/glyphhanger)
* [Transfonter (Online) – Modern and simple css @font-face generator](https://transfonter.org/)
* [woff2 (CLI) – Produce `.woff2` files](https://github.com/google/woff2)
