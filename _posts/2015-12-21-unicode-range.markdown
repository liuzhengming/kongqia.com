---
layout: post
title: unicode-range
date: 2015-12-21 00:45:29.000000000 +08:00
---

The **`unicode-range`** CSS descriptor sets the specific range of characters to be downloaded from a font defined by [`@font-face`](https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face "The @font-face CSS at-rule allows authors to specify online fonts to display text on their web pages. By allowing authors to provide their own fonts, @font-face eliminates the need to depend on the limited number of fonts users have installed on their computers. The @font-face at-rule may be used not only at the top level of a CSS, but also inside any CSS conditional-group at-rule.") and made available for use on the current page.

The purpose of this descriptor is to allow the font resources to be segmented so that a browser only needs to download the font resource needed for the text content of a particular page. For example, a site with many localizations could provide separate font resources for English, Greek and Japanese. For users viewing the English version of a page, the font resources for Greek and Japanese fonts wouldn’t need to be downloaded, saving bandwidth.

<table class="properties"><tbody><tr><th scope="row">Related [at-rule](https://developer.mozilla.org/en-US/docs/Web/CSS/At-rule)</th><td>[`@font-face`](https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face "The @font-face CSS at-rule allows authors to specify online fonts to display text on their web pages. By allowing authors to provide their own fonts, @font-face eliminates the need to depend on the limited number of fonts users have installed on their computers. The @font-face at-rule may be used not only at the top level of a CSS, but also inside any CSS conditional-group at-rule.")</td></tr><tr><th scope="row">[Initial value](https://developer.mozilla.org/en-US/docs/Web/CSS/initial_value)</th><td>`U+0-10FFFF`</td></tr><tr><th scope="row">Media</th><td>all</td></tr><tr><th scope="row">[Computed value](https://developer.mozilla.org/en-US/docs/Web/CSS/computed_value)</th><td>as specified</td></tr><tr><th scope="row">Canonical order</th><td>order of appearance in the formal grammar of the values</td></tr></tbody></table>
## Syntax

`<code class=" language-css"><span class="token comment" spellcheck="true">/* <unicode-range> values */</span><span class="token property">unicode-range</span><span class="token punctuation">:</span> U+<span class="token number">26</span><span class="token punctuation">;</span><span class="token comment" spellcheck="true">/* single codepoint */</span><span class="token property">unicode-range</span><span class="token punctuation">:</span> U+<span class="token number">0</span>-<span class="token number">7</span>F<span class="token punctuation">;</span><span class="token property">unicode-range</span><span class="token punctuation">:</span> U+<span class="token number">0025</span>-<span class="token number">00</span>FF<span class="token punctuation">;</span><span class="token comment" spellcheck="true">/* codepoint range */</span><span class="token property">unicode-range</span><span class="token punctuation">:</span> U+<span class="token number">4</span>??<span class="token punctuation">;</span><span class="token comment" spellcheck="true">/* wildcard range */</span><span class="token property">unicode-range</span><span class="token punctuation">:</span> U+<span class="token number">0025</span>-<span class="token number">00</span>FF, U+<span class="token number">4</span>??<span class="token punctuation">;</span><span class="token comment" spellcheck="true">/* multiple values can be separated by commas */</span><span class="token comment" spellcheck="true">/* Global values */</span><span class="token property">unicode-range</span><span class="token punctuation">:</span> inherit<span class="token punctuation">;</span><span class="token property">unicode-range</span><span class="token punctuation">:</span> initial<span class="token punctuation">;</span><span class="token property">unicode-range</span><span class="token punctuation">:</span> unset<span class="token punctuation">;</span>`

### Values

<dl><dt>*single codepoint*</dt><dd>A single Unicode character code point, for example `U+26`.</dd><dt>*codepoint range*</dt><dd>A range of Unicode code points. So for example, `U+0025-00FF` means *include all characters in the range `U+0025` to `U+00FF`*.</dd><dt>*wildcard range*</dt><dd>A range of Unicode code points containing wildcard characters, that is using the `'?'` character, so for example `U+4??` means *include all characters in the range `U+400` to `U+4FF`*.</dd></dl>### Formal syntax

[How to read CSS syntax.](https://developer.mozilla.org/docs/Web/CSS/Value_definition_syntax)

<unicode-range>[#](https://developer.mozilla.org/en-US/docs/CSS/Value_definition_syntax#Hash_mark_(.23) "Hash mark")


## Examples

We create a simple HTML containing a single [`<div>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/div "The HTML <div> element (or HTML Document Division Element) is the generic container for flow content, which does not inherently represent anything. It can be used to group elements for styling purposes (using the class or id attributes), or because they share attribute values, such as lang. It should be used only when no other semantic element (such as <article> or <nav>) is appropriate.") element, including an ampersand, that we want to style with a different font. To make it obvious, we will use a sans-serif font, *Helvetica*, for the text, and a serif font, *Times New Roman*, for the ampersand.

<div class="example">`<div>Me & You = Us</div>`

</div>In the CSS, you can see that we are in effect defining a completely separate [`@font-face`](https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face "The @font-face CSS at-rule allows authors to specify online fonts to display text on their web pages. By allowing authors to provide their own fonts, @font-face eliminates the need to depend on the limited number of fonts users have installed on their computers. The @font-face at-rule may be used not only at the top level of a CSS, but also inside any CSS conditional-group at-rule.") that only includes a single character in it, meaning that we don’t need to download the entire font to get what we want if it is a hosted font, and if it is a local font as in this example, we can at least cut down on extra markup and styles. We could also have done this by wrapping the ampersand in a [`<span>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/span "The HTML <span> element is a generic inline container for phrasing content, which does not inherently represent anything. It can be used to group elements for styling purposes (using the class or id attributes), or because they share attribute values, such as lang. It should be used only when no other semantic element is appropriate. <span> is very much like a <div> element, but <div> is a block-level element whereas a <span> is an inline element.") and applying a different font just to that, but that is an extra element and rule set.

<div class="example">```
@font-face {
  font-family: 'Ampersand';
  src: local('Times New Roman');
  unicode-range: U+26;
}

div {
  font-size: 4em;
  font-family: Ampersand, Helvetica, sans-serif;	
}```

### Reference result

![What the example should looks like if your browser supports it.](https://mdn.mozillademos.org/files/6043/Refresult.png)

### Live result

<iframe class="live-sample-frame sample-code-frame" frameborder="0" height="104" id="frame_Examples" src="https://mdn.mozillademos.org/en-US/docs/Web/CSS/%40font-face/unicode-range$samples/Examples?revision=967331" width="500"></iframe>

<div class="open-in-host-container"><button class="open-in-host">OPEN IN CODEPEN </button><button class="open-in-host">OPEN IN JSFIDDLE </button></div></div>
## Specifications

<table class="standard-table"><thead><tr><th scope="col">Specification</th><th scope="col">Status</th><th scope="col">Comment</th></tr></thead><tbody><tr><td>[CSS Fonts Module Level 3  
<small lang="en-US">The definition of ‘unicode-range’ in that specification.</small>](https://drafts.csswg.org/css-fonts-3/#descdef-font-face-unicode-range)</td><td><span class="spec-CR">Candidate Recommendation</span></td><td>Initial definition</td></tr></tbody></table>
## Browser compatibility

<div class="htab">[]()- [Desktop]()
- [Mobile]()

<div id="compat-desktop"><table class="compat-table"><tbody><tr><th>Feature</th><th>Firefox (Gecko)</th><th>Chrome</th><th>Internet Explorer</th><th>Opera</th><th>Safari</th></tr><tr><td>Basic support</td><td>[44](https://developer.mozilla.org/en-US/Firefox/Releases/44 "Released on 2016-01-26.") (44) [1]</td><td><span title="Please update this with the earliest version of support.">(Yes)</span>[2]</td><td>9.0</td><td><span title="Please update this with the earliest version of support.">(Yes)</span></td><td><span title="Please update this with the earliest version of support.">(Yes)</span></td></tr></tbody></table></div></div>[1] From Firefox 4 through Firefox 34, the `unicode-range` descriptor in [`@font-face`](https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face "The @font-face CSS at-rule allows authors to specify online fonts to display text on their web pages. By allowing authors to provide their own fonts, @font-face eliminates the need to depend on the limited number of fonts users have installed on their computers. The @font-face at-rule may be used not only at the top level of a CSS, but also inside any CSS conditional-group at-rule.") rules was parsed but the codepoint range ignored. From Firefox 35, `unicode-range` can be enabled on non-Linux platforms using the `layout.css.unicode-range.enabled` pref, which was on by default in nightly/developer builds. On Linux, this was possible from Firefox 41 onwards.

[2] Firefox and Chrome respect the `unicode-range` value when deciding which fonts to download (from Chrome 36, [http://crbug.com/247920](http://crbug.com/247920)). Safari and Internet Explorer ignore the unicode-range value when deciding which fonts to download but respect it when deciding which font to use.

未经允许不得转载：[空洽网](http://kongqia.com) » [unicode-range](http://kongqia.com/33665.html)


