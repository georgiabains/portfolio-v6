+++
title = "Configuration"
date = 2019-11-27

[taxonomies]
tagged = ["Accessibility", "HTML", "CSS"]

[extra]
excerpt = "Excerpt test. Let's make it a bit longer, enough to whet the appetite. After all, I'm going to be talking about so many interesting things."
+++

## H2

### H3

#### H4

##### H5

###### H6

## Heading

Paragraph example.  Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean pellentesque dignissim lobortis. Vestibulum vehicula lacus in velit cursus, eu auctor arcu sollicitudin. Curabitur tristique, tellus eu euismod pulvinar, ligula felis congue felis, quis elementum nulla nunc id lorem.

Phasellus sed sem lacinia, egestas sapien quis, dictum nunc. Etiam porta lectus id euismod pretium. Integer eget leo eget enim consectetur pharetra. Praesent urna massa, cursus quis tristique vel, congue non dui. Donec non turpis pharetra, mollis libero quis, suscipit est. Vivamus tincidunt dui velit, nec pharetra diam interdum in. Aliquam erat volutpat. Maecenas ullamcorper magna eu ipsum feugiat, eu tempus mauris luctus.

Line break.  
Here it is!

Got to test different emphases, like **bold text**, *italicised text*, and ***bolded & italicised text***.

> Of course we've got to have blockquotes.

Sometimes there'll be lists. Here's a list of my favourite types of tea:

- Black tea
- Green tea
- Matcha
- Peppermint tea

Or ordered lists. For example, here are the steps to making a cup of tea:

1. Boil water in a kettle.
2. Put a teabag in a mug.
3. Once the kettle has boiled, pour the water into the mug.
4. If having black tea, add milk to taste.

Naturally as a dev there'll be code blocks. Don't at click event listeners to `<div>` elements, use `<button>` (or `input`)! For example:

```html
<button type="submit">Submit form</button>
```

```js
// assume button has been queried.
button.addEventListener('click', () => console.log('yay'))
```

```css
body {
  margin: 0;
  padding: 0;
}
```

```rust
struct Person {
  name: String
}
```