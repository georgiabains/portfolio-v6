+++
title = "Making a PX to REM Converter in Rust"
date = 2026-07-01

[taxonomies]
tagged = ["Rust", "Desktop", "Accessibility"]
+++

I have a number of private repositories with different projects in different languages at varying stages of completion. A handful are almost complete and really only need a slight visual polish, while others are in "development hell" and have been subjected to _many_ iterations.

On a bit of a whim, partly fuelled by it being too hot to play games on my PC, I decided to de-scope and visually polish a simple Rust program I made a few months ago: a `px` to `rem` converter.

## Project summary
I recreated this [px to rem converter by NekoCalc](https://nekocalc.com/px-to-rem-converter) in Rust, using Slint for the UI, and added my own little spin.

Here's what it looks like! There's 3 input fields which control the following:
1. The base value in pixels (defaults to `16px`)
2. Target/computed value in `px`
3. Target/computed value in `rem`

{{ 
  image(
    alt="PX to REM program with a conversion for 16px to rem. The sentence summary reads '16 pixel(s) equals 1 rem unit(s) given a base value of 16 pixel(s).", 
    caption="Screenshot of my px to rem converter program.",
    src="./pxtoremprogram.png"
  )
}}

The `px` and `rem` input fields both update the other immediately. For example, given a base value of `16px`, entering `2` into the `rem` field would give you `32` in the `px` field.

I've got a [demo and accompanying transcript of some examples on the project Github](https://github.com/georgiabains/px-to-rem#demo).

## Accessibility highlights
Slint had some updates in the past few months, including some accessibility updates, so I was able to add an `aria-live` (`accessible-live` in Slint) region to announce changes. This was quite helpful as the dynamic input method was a bit confusing to navigate via tge screen readers I tested - Windows Narrator and NVDA. Now, the sentence at the bottom is a summary that announces the value of the pixels, rem units and base value.

Apart from that, keyboard and screen reader support was out-of-the-box!

## Rust and lessons learnt
I wanted to build a full suite of web-dev related tools in a program so that I could have all my converters and calculators and whatnot immediately available, built in Rust as a way to practice & learn the language, and without having to reject cookies. If I'm honest, rejecting cookies was the main reason, especially for the sites where they pre-select "legitimate interest" for roughly 200 different vendors. It just pisses me off.

Unfortunately, picking Slint for the UI was a mistake as I ended up writing way more in Slint's templating language than Rust, and more time in Slint's docs than Rust's docs. Really, there's only a handful of functions that were written in Rust, and it was really only some simple maths and string to float wrappers to interface with Slint.

Fortunately, there are some other crates for making desktop programs that involve using more Rust than not, so that's where I'll be turning my attention.