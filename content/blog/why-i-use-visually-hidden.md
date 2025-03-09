+++
title = "Why I use visually-hidden over aria-label"
date = 2025-03-09

[taxonomies]
tagged = ["Accessibility", "CSS", "HTML"]
+++

I've been guilty of shoving important or directive information behind an icon or two, and its definitely a popular way to "declutter" a visual interface. However, ensuring that the icon's meaning is also communicated via assistive technology is instrumental to ensuring that everyone understands your site.

A common method is using the `aria-label` attribute on the `<svg>` element, as it [provides the name for assistive technologies to announce](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Attributes/aria-label). Unfortunately, this approach can miss some demographics and as such I prefer using the `visually-hidden` paradigm (even though it's not a perfect solution).
## My gripes with aria-label
### Translation errors
[`aria-label` isn't always translated by assistive devices](https://adrianroselli.com/2019/11/aria-label-does-not-translate.html), which can cause a jarring and confusing experience for users that don't speak the primary language of the site. I don't deal with this on a day-to-day basis, as Shopify/Liquid expose translation strings to developers and store owners, so the chance of a label being is missed is quite low. However, I think that building robust coding practices is good for any developer.

`aria-labelledby`, where the contents of this attribute map to an ID on the page, is a suitable alternative. In practice (especially with conditional elements in Shopify), these IDs can go missing, or point to a duplicated element ID. If `<span>` isn't feasible for any reason, this is the labelling method I use.
### Poor global browser & assistive technology support
As browsers have grown and developed, so too has assistive technology and their interaction and support with various browsers in the past. While I don't support supporting Internet Explorer, various factors can prevent many people from accessing the latest update of the software they use to navigate the internet.

These older versions are effectively time capsules, and if `aria-label` was not supported then, it will not be now. Accessibility includes making sure that users without the latest hardware or software updates are able to navigate websites, in some form.

I use [PowerMapper's assistive techology tests](https://www.powermapper.com/tests/) when determining which attributes or elements are viable for a given site. I try to stay within a few years, and a generally positive and/or improving trend for support.
### Developer misuse
Assistive technology announces element types alongside its content. As an example, `<a>` elements will be announced as "example label, link" or "link, example label." `<button>` elements would be "example label, button" or "button, example label."

Yet too often, I've seen developers include the element type in the `aria-label`, such as `<a href="" aria-label="Link to destination">destination</a>` or `<button type="button" aria-label="button for action">action</button>`. This leads to repeated text, where "link," or "button" are repeated, and this repetition worsens a user's experience with the site.
## How does visually-hidden solve all that?
`visually-hidden` is shorthand for a CSS class called `visually-hidden` that uses CSS to hide or clip text so that it doesn't display on the screen yet its still rendered and announced to assistive devices. The reason I prefer this method is that it solves my gripes with `aria-label`:

1. It will be translated by any translation software because it is text rendered in HTML
2. It has global browser and assistive technology support because it is text rendered in HTML.
3. Developer's are less likely to misuse this class, because it is text rendered in HTML.
	1. This is anecdotal, so here's a pinch of salt, however I've never had to request a developer to edit `visually-hidden` text to omit the word "link" or "button."

To be clear, "text rendered in HTML" refers to text that without any CSS property (i.e. `display: none;` or `visibility: hidden;`), would be visually displayed to an end user, and without `aria-hidden="true"` would be announced to assistive devices.

Here's the current CSS I use:
```css
.visually-hidden {
  clip: rect(0 0 0 0);
  clip-path: inset(50%);
  height: 1px;
  overflow: hidden;
  position: absolute;
  white-space: nowrap;
  width: 1px;
}
```

Here's a working example of a link and button next to one another. I'm using icons within a header for my example, with a link to redirect the user to an account page, and a button to open a cart drawer:
```html
<a href="/account">
  <span class="visually-hidden">My account</a>
  <svg aria-hidden="true" ...>...</svg> <!-- Account icon, such as an outline of a person -->
</a>

<button aria-expanded="false" aria-haspop="dialog" type="button" data-cart-drawer>
  <span class="visually-hidden">Cart</span>
  <svg aria-hidden="true" ...>...</svg> <!-- Cart icon, such as a trolley or bag -->
</button>
```
## Issues with visually-hidden
While I appreciated its simplicity, it's not without its downsides. As stated in Scott O'Hara's article [Visually hidden content is a hack that needs to be resolved, not enshrined](https://www.scottohara.me/blog/2023/03/21/visually-hidden-hack.html), it is a workaround for browser and language limitations, pitfalls in designs and developer's respecting IDs (where `aria-labelledby` could be used). Unfortunately, most developers are only able to control what IDs are added where, and that relies on descriptive content existing elsewhere on a page. Within a Shopify context, most of the content will be provided and edited by a client, so we can't always rely on context to stay the same, and while we can make some suggestions to designs, we would rarely have a final say.

As an aside, I appreciate that these last two points could be resolved with instruction and teaching more people about accessibility and how it benefits everyone. I've had some success in the past, such as creating accessibility guidelines, but I'm working on a bit more of a thorough approach right now. Hopefully I'll be able to share a rough overview of that process!

Back to `visually-hidden`, for the sake of as-close-to-global-support-as-possible, an easy-to-implement-solution, a solution that fits in nicely to existing workflows, and until we have something better (from browsers!), this is the paradigm I'll be championing.
## TLDR; 

It's text rendered in HTML.