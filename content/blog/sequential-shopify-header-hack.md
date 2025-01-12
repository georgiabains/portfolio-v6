+++
title = "Sequential Shopify header hack"
date = 2025-01-12

[taxonomies]
tagged = ["Accessibility", "Shopify"]
+++
Keeping heading elements (`h1` through `h6`) sequential can be tricky when using Shopify Sections Everywhere, as their placement and frequency are entirely up to the client, or end-theme-user.

Since section headings and subheadings are often optional, assigning hardcoded headings may result in a non-sequential heading order. For example, hardcoding the first heading in a section as `<h2>`, as assigning consequent subheadings as `<h3>` would throw the order off if a client leaves that first heading blank.

The solution I like to use is to assign the heading and/or subheading element to a variable. I'll use an example section that has blocks to demonstrate the code:

```html
{%- liquid
  assign subheading_element = 'h2'

  if section.settings.heading != blank
    assign subheading_element = 'h3'
  endif
-%}

<section>
  {% if section.settings.heading != blank %}
    <h2>{{ section.settings.heading }}</h2>

    ...
    
    {% for block in section.blocks %}
      <{{ subheading_element }}>{{ block.settings.heading }}</{{ subheading_element }}>
    {% endfor %}
  {% endif %}
</section>
```

If clients require a specific font size or design, then using a helper class ensures that the code is semantic and accessible, while upholding branding requirements.