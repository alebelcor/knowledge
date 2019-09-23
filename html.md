# HTML

## Sections

[The `article` element](https://html.spec.whatwg.org/#the-article-element) represents a complete, or self-contained, composition in a document, page, application, or site and that is, in principle, independently distributable or reusable.

[The `section` element](https://html.spec.whatwg.org/#the-section-element) represents a generic section of a document or application. A section, in this context, is a thematic grouping of content, typically with a heading.

[The `nav` element](https://html.spec.whatwg.org/#the-nav-element) represents a section of a page that links to other pages or to parts within the page: a section with navigation links.

[The `aside` element](https://html.spec.whatwg.org/#the-aside-element) represents a section of a page that consists of content that is tangentially related to the content around the `aside` element, and which could be considered separate from that content. Such sections are often represented as sidebars in printed typography.

[The `header` element](https://html.spec.whatwg.org/#the-header-element) represents a group of introductory or navigational aids.

[The `footer` element](https://html.spec.whatwg.org/#the-footer-element) represents a footer for its nearest ancestor sectioning content or sectioning root element. A footer typically contains information about its section such as who wrote it, links to related documents, copyright data, and the like.

[More examples](https://html.spec.whatwg.org/#usage-summary-2).

## Grouping content

[The `menu` element](https://html.spec.whatwg.org/#the-menu-element) represents a toolbar consisting of its contents, in the form of an unordered list of items (represented by `li` elements), each of which represents a command that the user can perform or activate.

[The `main` element](https://html.spec.whatwg.org/#the-main-element) represents the dominant contents of the document.

[The `div` element](https://html.spec.whatwg.org/#the-div-element) has no special meaning at all

[More examples](https://html.spec.whatwg.org/#usage-summary).

## Text-level semantics

[The `em` element](https://html.spec.whatwg.org/#the-em-element) represents stress emphasis of its contents.

[The `strong` element](https://html.spec.whatwg.org/#the-strong-element) represents strong importance, seriousness, or urgency for its contents.

[The `small` element](https://html.spec.whatwg.org/#the-small-element) represents side comments such as small print.

[The `cite` element](https://html.spec.whatwg.org/#the-cite-element) represents the title of a work (e.g. a book, a song, a film, etc.).

[The `abbr` element](https://html.spec.whatwg.org/#the-abbr-element) represents an abbreviation or acronym, optionally with its expansion (with `title` attribute).

[The `time` element](https://html.spec.whatwg.org/#the-time-element) represents its contents, along with a machine-readable form of those contents in the `datetime` attribute.

[The `i` element](https://html.spec.whatwg.org/#the-i-element) represents a span of text in an alternate voice or mood, or otherwise offset from the normal prose in a manner indicating a different quality of text.

[The `b` element](https://html.spec.whatwg.org/#the-b-element) represents a span of text to which attention is being drawn for utilitarian purposes without conveying any extra importance and with no implication of an alternate voice or mood, such as key words in a document abstract, product names in a review, actionable words in interactive text-driven software, or an article lede.

[The `u` element](https://html.spec.whatwg.org/#the-u-element) represents a span of text with an unarticulated, though explicitly rendered, non-textual annotation.

[The `span` element](https://html.spec.whatwg.org/#the-span-element) doesn't mean anything on its own.

[More examples](https://html.spec.whatwg.org/#usage-summary).

## Scripting

[The `script` element](https://html.spec.whatwg.org/#the-script-element) allows authors to include dynamic script and data blocks in their documents.

### `async` and `defer`

`async` and `defer` are boolean attributes that indicate how the script should be evaluated. Classic scripts may specify `defer` or `async`, but only when the `src` attribute is present.

With `<script>`, parsing is interrupted by fetching and execution.

With `<script defer>`, fetching is parallel to parsing and execution takes place after all parsing has finished.

With `<script async>`, fetching is parallel to parsing but once it finishes parsing is interrupted to execute the script (potentially before parsing completes).

The story for `<script type="module">` is similar to `<script defer>`, but the dependencies will be fetched as well.

The story for `<script type="module" async>` is similar to `<script async>` with the extra dependency fetching. (The `defer` attribute has no effect on module scripts.)

![Schematic diagram summarizing the above](https://html.spec.whatwg.org/images/asyncdefer.svg)
