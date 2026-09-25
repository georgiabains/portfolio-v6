+++
title = "A small reminder to consider accessibility for all features"
date = 2026-09-25

[taxonomies]
tagged = ["Accessibility", "CSS", "HTML"]
+++

## Problem: The unassuming feature
I worked on a straightforward feature recently, where a product had a "scale" comprised of three options, and the product's selected option was expressed via a dark underline. The feature didn't include any links or buttons, there wasn't anything for the end-user to select, and all the options sat within a `flex` container, so content would adjust based on zoom. Truly, the only programmatic differentiation between each scale option was a line of CSS that specified the dark underline. 

Hang on a minute, this means that one of the product's selling points was only communicated visually. How would a screen reader like VoiceOver announce this? NVDA? Would they be able to identify which option was selected, given that the only difference was CSS? (*Hint: no*)

## Solution: Sentence-based explanation
I ended up adding an `aria-label` that announced the name of the scale, the selected option on the scale, and repeated all options in order. Using a hot sauce as an example, the resulting announcement was something like:

> This product is "spicy" on the spiciness scale, given the options "mild, moderate, spicy."

In hindsight, using `aria-describedby` is probably more appropriate, that's one for me to review on Monday.