# Web Performance

## CSS

No JS technique for loading CSS asynchronously:

```html
<link rel="stylesheet" href="/path/to/file.css" media="print" onload="this.media='all'">
```

## Images

Non-critical `<img>` should be lazy loaded natively by the browser with [`loading="lazy"`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/img#attr-loading). And set their decoding be non-blocking with [`decoding=”async”`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/img#attr-decoding).

Favor using the [`<picture>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/picture) tag for displaying responsive images in different next-gen formats depending on what the browser supports.

The order of the [`<source>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/source) tags in `<picture>` should depend on the output size of the different image formats, as the browser will grab the first supported format from top to bottom, i.e. the smallest should be at the top.

```html
<picture>
  <source
    media="(min-width: 768px)"
    type="image/avif"
    srcset="my-larger-image.avif"
  >
  <source
    media="(min-width: 768px)"
    type="image/webp"
    srcset="my-larger-image.webp"
  >
  <source
    media="(min-width: 768px)"
    srcset="my-larger-image.jpg"
  >
  <source
    type="image/avif"
    srcset="my-base-image.avif"
  >
  <source
    type="image/webp"
    srcset="my-base-image.webp"
  >
  <img
    src="my-base-image.jpg"
    alt="Alternative text for accessibility"
    loading="lazy"
    decoding="async"
  >
</picture>
```

### Photographic images

| Format | Lossless | Alpha | Animation | Notes |
|:------:|:--------:|:-----:|:---------:|:-----:|
| [AVIF](https://en.wikipedia.org/wiki/AV1#AV1_Image_File_Format_(AVIF)) | **✓** | **✓** | **✓** | No progressive mode. [Browser support](https://caniuse.com/avif) |
| [WebP](https://en.wikipedia.org/wiki/WebP) | **✓** | **✓** | **✓** | No progressive mode. [Browser support](https://caniuse.com/webp) |
| [JPEG](https://en.wikipedia.org/wiki/JPEG) | **x** | **x** | **x** | Progressive mode. All browsers support it |

### Non-photographic images

Refers to synthetic/vector/sharp edges/text images.

Depending on your usage, your best option may be embedded SVG when critical, and in `<img>` when non-critical. It is technically lossless. And since SVG is just text, it can be [optimized](https://jakearchibald.github.io/svgomg/).

If you don't need to re-scale your (non-photographic) image consider compressing it as AVIF, WebP (since they both support transparency) and [PNG](https://en.wikipedia.org/wiki/Portable_Network_Graphics). These may yield a smaller file size than SVG.

### Animated

AVIF and WebP support animation.

[APNG](https://en.wikipedia.org/wiki/APNG) is another option ([browser support](https://caniuse.com/apng)), but usually yields a bigger file size than [GIF](https://en.wikipedia.org/wiki/GIF).

### Future

In the not-so-distant future, the format to rule them all may be [JPEG XL](https://jpeg.org/jpegxl/) ([browser support](https://caniuse.com/jpegxl)).

It supports alpha and other channels, has high bit depth, supports lossless, animation, progressive mode, it's responsive by design, high quality, and legacy-friendly.

With all of that it can replace JPEG, PNG, GIF, and others.

### Misc

Avoid [JPEG 2000](https://caniuse.com/jpeg2000). It's only supported in Safari.

Avoid [JPEG XR](https://caniuse.com/jpegxr). It's only supported in IE 11 and older.

## Web Fonts

### Formats

Use <abbr title="Web Open Font Format">WOFF</abbr>. It has the widest browser support and yields the smallest file size over other formats.

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

If you need to support IE 11, add [WOFF 1](https://caniuse.com/woff) as fallback:

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

Note: `crossorigin` and `crossorigin=""` are the same as `crossorigin="anonymous"` (the default).

### Character ranges

Use the [`unicode-range`](https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face/unicode-range) descriptor to define one, or more, specific ranges of characters to be used from a font defined by `@font-face`. If the page doesn't use any character in the range, the font is not downloaded; if it uses at least one, the whole font is downloaded.

Google Fonts outputs different ranges using `unicode-range`: [Example](https://fonts.googleapis.com/css2?family=Roboto&display=swap)

### Subsetting

Subsetting allows you to include only the characters/glyphs you want instead of a full font file.

For example, subsetting to basic latin characters for an English only site.

See [Links](#Links) section for tools on this.

### Misc

Use long [HTTP caching](https://web.dev/http-cache/#cache-control) for fonts, since they are static resources that don't see frequent updates.

Avoid using the Google Fonts service and [self-host the fonts instead](https://wicki.io/posts/2020-11-goodbye-google-fonts/).

Avoid using the `local()` function, in `@font-face`, to prevent showing potentially unexpected locally installed fonts.

Consider using [variable fonts](https://web.dev/variable-fonts/) ([browser support](https://caniuse.com/variable-fonts)).

## Links

* [Ezgif (Online) – Animated GIF editor and GIF maker | convert, edit](https://ezgif.com/)
* [google-webfonts-helper (Online) – Get (Google Fonts) eot, ttf, svg, woff and woff2 files + CSS snippets](https://github.com/majodev/google-webfonts-helper)
* [ImageMagick (CLI) – Create, edit, compose, or convert digital images](https://imagemagick.org/index.php)
* [fontTools (CLI) – a library for manipulating fonts](https://github.com/fonttools/fonttools)
* [Font Squirrel (Online) – Create Your Own @font-face Kits | convert, subset](http://www.fontsquirrel.com/tools/webfont-generator)
* [glyphhanger (CLI) – Your web font utility belt](https://github.com/filamentgroup/glyphhanger)
* [Photopea (Online) – Online Photo Editor | convert, resize, crop, etc.](https://www.photopea.com/)
* [Squoosh (Online) – Compress and compare images with different codecs, right in your browser | compress, convert, resize](https://squoosh.app/)
* [The Simplest Way to Load CSS Asynchronously – Article](https://www.filamentgroup.com/lab/load-css-simpler/)
* [Transfonter (Online) – Modern and simple css @font-face generator | convert, subset](https://transfonter.org/)
* [woff2 (CLI) – Produce `.woff2` files](https://github.com/google/woff2)
