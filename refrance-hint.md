# Field Notes: Hints

How to use this: for each level, try to build the section yourself using only Hint 1. If you are stuck, read Hint 2. Read the full explanation last, or to check your work against `field-notes.html`.

Each level has three parts:
- **Hint 1:** a subtle nudge.
- **Hint 2:** a stronger hint that names the tools to use.
- **Explanation:** everything used in that section, and why.

---

## Page Skeleton (the head, header, main and footer)

**Hint 1:** Before any visible content exists, the browser needs to be told what kind of document this is. And the page has two halves: one the visitor never sees, and one they do.

**Hint 2:** Type `!` in VS Code and press Enter for the boilerplate. Put the CSS in the invisible half. Inside the visible half, use landmark tags (not `div`s) for the top, the main content and the bottom.

**Explanation**
- `<!DOCTYPE html>` tells the browser this is HTML5.
- `<html lang="en">` is the root element, and `lang` declares the language.
- `<head>` holds things that are not displayed: `<meta charset="UTF-8">` (character encoding), the viewport meta tag (makes phones use their real screen width), `<title>` (the browser tab text) and the `<style>` block (internal CSS).
- `<body id="top">` holds everything visible. The `id` lets links like `href="#top"` jump back to it.
- `<header>`, `<nav>`, `<main>` and `<footer>` are the page's landmarks. There is only one `<main>`.
- `* { box-sizing: border-box; }` uses the universal selector so padding and border never make a box wider than its set width.
- The `body` rule sets the margin, background, text colour, font and line height for the whole page.
- `.wrap { width: 90%; max-width: 900px; margin: 0 auto; }` is a reusable centred column. `margin: 0 auto` only centres because the width is set.
- The `nav` links use `href="#l1"` style links, called page jumps. Each one matches an `id` on a section further down.
- `&nbsp;` in the title keeps "So" and "Far" together, and `&amp;` writes an ampersand safely.

---

## Level 1: Words on a page

**Hint 1:** You already know how to write a heading and a paragraph. What if you want a word to stand out, or you need to show a symbol the browser would treat as code?

**Hint 2:** Look at text-formatting tags (`strong`, `em`, `ins`), the two tags that need no closing tag, and the `&name;` codes. For the last paragraph, remember CSS can be written directly on a tag.

**Explanation**
- `<h1>` to `<h6>`: heading levels. Only some are shown here, and there is one `h1` for the page.
- `<p>`: a paragraph. Browsers add default margins to it (the user-agent stylesheet).
- `<strong>` (important, bold), `<em>` (emphasis, italic) and `<ins>` (inserted text, underlined).
- `<br>` forces a line break and `<hr>` draws a horizontal line. Both are void elements, meaning they have no closing tag.
- `<!-- ... -->` is a comment. It is visible in the source but never on the page.
- Character entities: `&lt;` `<`, `&gt;` `>`, `&amp;` `&`, `&quot;` `"`, `&copy;` ©, `&trade;` ™, `&mdash;` the long dash, `&nbsp;` a non-breaking space.
- Normal extra spaces in code collapse into one, but repeated `&nbsp;` keeps them.
- `style="color: blue; background-color: yellow;"` is inline CSS. `color` changes the text, and `background-color` changes what is behind it.

---

## Level 2: Selectors and colours

**Hint 1:** You want to style one specific thing, a group of things, and every thing of one kind, without writing a `style` attribute on each tag.

**Hint 2:** You need a tag selector, a `.class` selector and a `#id` selector. For colours, write the same colour in three different formats. The `<span>` tag is useful for styling part of a sentence.

**Explanation**
- Tag selector: `p { ... }` styles every `<p>`. (In this file, `a { color: ... }` and `h1, h2, h3 { ... }` do the same for links and headings.)
- Id selector: `#special { color: #2F5BEA; }` matches the one element with `id="special"`. An id should be used once per page.
- Class selector: `.highlight { color: #F2545B; }` matches every element with `class="highlight"`. A class can be reused anywhere.
- Colour formats: keyword (`yellow`), hex (`#2EC4B6`) and `rgb(255, 210, 63)`. All three work for both `color` and `background-color`.
- `<span>` is an inline element with no meaning of its own. It exists to attach a class or id to part of a line.
- Three ways to write CSS: inline (`style=""`), internal (the `<style>` block in the head) and external (a `.css` file linked with `<link rel="stylesheet" href="style.css">`). External is best for multi-page sites because one change updates every page.

---

## Level 3: Lists and links

**Hint 1:** Think about three different reasons to list things: the order doesn't matter, the order matters, or each item has a name and a description. For the links, ask what a browser needs to find another page, an email address, or a spot on the same page.

**Hint 2:** Use `ul`, `ol` and `dl` (with `li`, `dt` and `dd`). For links, use `<a href="...">` with a different kind of `href` each time, and the `target` attribute for the tab behaviour.

**Explanation**
- `<ul>` with `<li>`: unordered list (bullets).
- `<ol>` with `<li>`: ordered list (numbers).
- `<dl>` with `<dt>` (term) and `<dd>` (description): description list, good for glossaries.
- `<a href="...">` is a link. The kinds used here:
  - `./Pages/about.html`: relative to the current folder.
  - `/4_HTML/Pages/about.html`: root-relative, starts from the root of the site.
  - `https://www.google.com/`: absolute, with the full address and protocol.
  - `mailto:` opens an email app. `tel:` starts a call.
  - `#top`: a page jump to the element with `id="top"`.
- `target="_blank"` opens a new tab. `target="_self"` is the default and opens in the same tab. `_parent` and `_top` only matter when a page is inside an iframe.
- `a:hover` (in the CSS) changes the link colour while the mouse is over it, and `a:active` while it is pressed.

---

## Level 4: Semantic structure

**Hint 1:** The same content could be built from `div`s, but then neither the browser nor another developer would know what each piece is for. Which pieces here are stand-alone, and which are only loosely related?

**Hint 2:** Use `article` for self-contained content and `aside` for a side note. You can put a `header` and `footer` inside an `article`. Give them visible borders so you can see the structure.

**Explanation**
- `<section>`: a thematic group of content, usually with its own heading. Every level on this page is one.
- `<article>`: self-contained content that would make sense on its own, like a blog post or product card.
- `<header>` and `<footer>` can appear more than once, including inside an `article`.
- `<aside>`: content indirectly related to the main content, like a tip or sidebar.
- Semantic tags look the same as `div`s until you add CSS. They help readability, accessibility and search engines.
- CSS: `article` gets a white background, a border and padding. `aside` gets a dashed border and a yellow background. `.level` adds padding and a top border to every section. `.tag` styles the level badge, and `.note` styles the tip boxes.

---

## Level 5: Images and embeds

**Hint 1:** Two of the things you need here are pictures and another website shown inside yours. One of the images should fail on purpose: what does the browser show then?

**Hint 2:** Use `<img>` with `src`, `alt`, `width` and `height`, and `<iframe>` with `src`, `width` and `height`. YouTube and Google Maps both give you an embed-style address.

**Explanation**
- `<img>` is a void element. `src` is the file location, `alt` is the text shown if the image cannot load (and read by screen readers), and `width` and `height` set the size.
- The first image uses a `data:` address, meaning the picture is written inside the HTML itself, so no file is needed.
- The second image points to a file that does not exist. The browser shows its `alt` text instead.
- `<iframe src="...">` embeds another page. It is used here for a YouTube video (`/embed/` address) and a Google Maps location (`output=embed`).
- Some sites, like Amazon, block being embedded, so an iframe of them stays empty.
- `title` on an iframe describes it for assistive technology.
- CSS: `img { border: 3px solid ...; }` and `iframe { border: 0; max-width: 100%; }`. The `max-width` stops it overflowing on small screens.

---

## Level 6: Forms

**Hint 1:** A form is a conversation: each question needs a place to answer it. Some questions allow one answer, some allow many, and some should not be skipped.

**Hint 2:** Wrap everything in `<form>`. Use `<input>` with different `type` values, `<select>` with `<option>`, and matching `name` attributes on radios and checkboxes. Finish with both kinds of submit.

**Explanation**
- `<form action="#l6">`: wraps the inputs. `action` is where the data is sent. Here it jumps back to this section, because there is no backend yet.
- `<input type="text">` with `placeholder`: a text box with grey hint text.
- `<input type="number" required>`: only accepts numbers, and the browser blocks submission if it is empty.
- `value="Delhi"`: a preset answer.
- `<select>` with `<option>`: a dropdown of choices.
- `type="radio"`: one choice only. Radios with the same `name` form a group.
- `type="checkbox"`: any number of choices.
- `<label for="id">` pairs with an input's `id`, so clicking the text focuses the input.
- `<input type="submit">` and `<button type="submit">` both submit the form. The button can hold any content.
- CSS: `input, select` get padding and margins. Forms are covered again properly in the JavaScript section.

---

## Level 7: The box model

**Hint 1:** Every element is a stack of rectangles. Try giving a plain paragraph a colour and inspect it in DevTools to see which rectangles exist. Also ask: what happens to a box's real size when you add padding?

**Hint 2:** You need `padding`, `border`, `margin`, shorthand with 1 to 4 values, `margin: 0 auto` with a width, two stacked paragraphs with vertical margins, `box-sizing`, and `display`.

**Explanation**
- Layers from the inside out: content, padding (space inside the background), border, margin (space outside, with no background).
- `.box`: `padding: 20px; border: 5px solid black; margin: 20px;` shows all four layers.
- Shorthand: `padding: 10px 40px 10px 5px;` means top, right, bottom, left. Two values are top/bottom and left/right. Three are top, left/right and bottom. One value applies to all sides.
- `.centered`: `width: 300px; margin: 0 auto;` centres a block. Auto only works for left and right, and only when a width is set.
- Margin collapsing: a bottom margin of 30px above a top margin of 20px gives a gap of 30px, not 50px. Padding and left/right margins do not collapse.
- `box-sizing: content-box` (the default): width covers only the content, so padding and border make the box bigger (300 + 40 + 10 = 350px). `border-box`: width includes padding and border, so the box stays 300px.
- Block vs inline: a `div` takes a full line, and `span`s sit side by side. `width` only works on block elements.
- `display: block` and `display: inline` swap this behaviour. `display: none` removes the element completely, including its space.

---

## Level 8: The cascade and units

**Hint 1:** When two rules disagree about the same property, something has to win. Build a few elements where more and more rules apply to them and see how the colour changes. For units, imagine resizing the window.

**Hint 2:** Apply a tag rule, then a class rule, then an id rule, then an inline style, then `!important`. For units, make four bars using `px`, `%`, `vw` and `vh`, and drag the window size.

**Explanation**
- Specificity order, weakest to strongest: browser default (user-agent stylesheet), universal `*`, tag, class, id, inline style, `!important`.
- `h5 { color: blue; }`: only a tag rule, so it is blue.
- `.battle { color: orange; }`: a class beats a tag, so the second heading is orange.
- The third heading has a class, an id (`#winner`), an inline `color: red` and `!important` on the id rule. `!important` wins over inline, so it is teal.
- Units:
  - `px`: a fixed size that never changes.
  - `%`: relative to the parent's width. Resize the window and the bar follows the parent.
  - `vw`: a percentage of the window width (`30vw` is 30%).
  - `vh`: a percentage of the window height.
- Only `px` stays the same when the window is resized.

---

## Level 9: Rounded corners, backgrounds, opacity and states

**Hint 1:** Think about softening a square, filling a box with a picture-like background, making something see-through in two different ways, and reacting when the mouse touches or presses a button.

**Hint 2:** Use `border-radius` (compare px with %), `background-image` with `background-size` and `background-position`, `opacity` vs `rgba()` on a dark box, and `:hover` and `:active` with `scale`.

**Explanation**
- `border-radius: 20px;` rounds the corners by a fixed amount. `border-radius: 50%;` on a square makes a circle.
- `background-image: linear-gradient(...)` fills the box. A `url(...)` photo works the same way. `background-size: cover` fills the box without gaps, and `background-position: center` keeps the middle visible.
- `opacity: 0.5` fades the whole element, including its text and children.
- `background-color: rgba(0, 0, 0, 0.5)` is `rgb` plus a fourth value for transparency. It fades only the background, so the text stays solid.
- The yellow `.stripes` box sits behind both dark boxes so you can see the transparency.
- `:hover` applies while the mouse is over the element. `:active` applies while it is pressed.
- `scale: 1.25` enlarges the element and `scale: 0.75` shrinks it. Together they give the button's idle, hover and pressed states.

---

## Level 10: Position

**Hint 1:** So far, everything sits where the HTML order puts it. What if you want to nudge one box, pin one inside another, stack two on top of each other, or keep one on screen while scrolling?

**Hint 2:** You need `position` with `relative`, `absolute` and `fixed`, plus `top`, `left`, `bottom`, `right` and `z-index`. Put `position: relative` on the parent of the absolute boxes.

**Explanation**
- `static`: the default. The element is in the normal flow and `top`/`left` do nothing.
- `relative`: moves from its normal spot, and the gap it leaves behind stays. `.shifted` uses `top: 10px; left: 30px;`.
- `absolute`: removed from the flow and placed relative to the nearest positioned ancestor. `.stage` has `position: relative`, so `.pa` and `.pb` are measured from its corner. Without that, they would be measured from the page.
- `z-index`: controls overlap. `.pa` and `.pb` overlap, and `.pb` has `z-index: 1`, so it sits on top. Without it, the later element in the HTML is on top.
- `fixed`: placed relative to the window and stays put while scrolling. `.to-top` uses `position: fixed; right: 16px; bottom: 16px;`.

---

## Level 11: Flexbox

**Hint 1:** Centering and spreading boxes used to be awkward. There is one property on the parent that changes how all its children behave, without touching them.

**Hint 2:** Put `display: flex` on the container. Use `justify-content` for the main direction, `align-items` for the other one, and `flex-direction` to change which direction is the main one. Give the container a height to see vertical effects.

**Explanation**
- `display: flex` on `.flex` turns its children into a row of flex items. They sit side by side instead of stacking.
- `justify-content` controls the main axis (horizontal by default):
  - `center` groups the items in the middle.
  - `space-between` pushes the first and last items to the edges, with equal gaps between.
  - `space-around` puts equal space around each item, so the edges get half the gap.
- `align-items: center` controls the cross axis (vertical by default). It only shows when the container has a height, like `.tall` (160px).
- `flex-direction: column` swaps the axes: the items stack, `justify-content` now works vertically and `align-items` horizontally.
- `.center-all` has `justify-content: center; align-items: center;` and a height. This centres a box both ways, the problem that used to be nearly impossible.
- `.item` is only the look of each box: padding, margin, colour.

---

## Level 12: Smarter selectors and responsive design

**Hint 1:** You want to style every other item, or the third one, without adding a class to each. And you want the page to change for narrow screens, including hiding something there.

**Hint 2:** Use `:nth-child()` (with a number and with `even`), compare it with `:nth-of-type()`, and write `@media` rules using `max-width`, `min-width` and the `width <=` form. Hide with `display: none`.

**Explanation**
- `.n:nth-child(3)` picks the element that is the third child of its parent. `:nth-child(even)` picks every even position. The class `.n` is only there so these rules don't affect the lists in Level 3.
- `nth-child` counts every kind of element. `nth-of-type` counts only elements of the same tag. In the `.t` group (two `h4`s then two `p`s), `.t:nth-child(3)` is the first `p` (green), while `.t:nth-of-type(2)` is the second `h4` and the second `p` (yellow background).
- Media queries apply CSS only when a condition is true:
  - `@media (max-width: 600px)`: windows 600px wide or less. Here it changes the background, swaps the two `only-` paragraphs with `display: none`, wraps flex items and stacks the shop cards.
  - `@media (min-width: 601px)`: windows wider than 600px. It targets the opposite range.
  - `@media (width <= 400px)`: the modern range syntax. It does the same job as `max-width` and shrinks the `h1`.
- The viewport meta tag in the head is required for these queries to work on real phones.
- Design question to think about: mobile-first means writing the small-screen CSS first and adding `min-width` rules for bigger screens.

---

## Level 13: Final build, a mini shop

**Hint 1:** This level is a landing page: a bar at the top, a big banner with text over it, three product cards and a footer. Almost everything is something you built in an earlier level.

**Hint 2:** Navbar: flex with `space-between`. Banner: `position: relative`, a gradient background, and an absolute overlay with `rgba`. Text on top: flex column, centred. Cards: flex row, fixed width, `border-radius`, `overflow: hidden`. Badge: absolute inside a relative card.

**Explanation**
- `.shop-nav`: `display: flex; justify-content: space-between; align-items: center;` puts the brand on the left and links on the right, vertically centred.
- `.shop-hero`: `position: relative` with a set height, `background-image` (gradient), `background-size: cover` and `background-position: center`.
- `.overlay`: `position: absolute; top: 0; left: 0; width: 100%; height: 100%;` with `rgba(0, 0, 0, 0.4)` darkens the banner so the text is readable.
- `.hero-content`: `position: relative` keeps it above the overlay. `display: flex; flex-direction: column; justify-content: center; align-items: center; height: 100%;` centres the heading, text and button in the banner.
- `.cta`: the button-like link, with `border-radius` for the pill shape.
- `.products`: `display: flex; justify-content: center;` lines up the cards.
- `.card`: fixed `width: 200px`, `border`, `border-radius: 14px`, and `overflow: hidden` so the image area's corners are clipped to the rounded card. `margin: 0 8px` spaces them out.
- `.badge`: `position: absolute; top: 10px; left: 10px;` inside the card (which is `position: relative`), with a semi-transparent red `rgba`, padding and `border-radius: 20px`.
- `.card:hover`: changes the border colour on hover.
- `.footer`: centred text, padding, a muted background, and `&copy;` and `&trade;` entities.
- The `max-width: 600px` media query switches `.products` to a column and stacks the navbar, so the shop works on phones.
- Everything together: semantic structure, box model, units, position, flexbox, `border-radius`, background-image, `rgba`, pseudo-classes and media queries.

---

## Page footer and the "Top" button

**Hint 1:** The page should end with a footer, and one control should stay visible no matter where you scroll.

**Hint 2:** A `footer` tag with entities for the copyright, and an `<a>` styled with `position: fixed`.

**Explanation**
- `<footer class="wrap">` closes the page and uses `&copy;`, `&trade;` and `&mdash;`.
- `<a class="to-top" href="#top">` is a link that jumps to `id="top"` on the body. `position: fixed` keeps it in the corner.
- `border-radius: 20px` makes it a pill, `text-decoration: none` removes the underline, and `.to-top:hover` changes the text colour.