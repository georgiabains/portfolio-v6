+++
title = "Accessibility is technology, technology is accessibility"
date = 2024-12-31

[taxonomies]
tagged = ["Accessibility"]
+++

I'm quite vocal about accessibility, and surround my online spaces with other like-minded people, so I'm usually surprised when I come across a comment or statement that outright rejects accessibility as a worthy investment. These people may use phrases such as "disabled people aren't my target audience," or sayings such as "if you make something for everyone, you make it for no one." I have a hard time seeing accessibility from this point of view for one simple reason: accessibility is technology, and technology is accessibility.

## Definitions
[Cambridge dictionary defines "technology"](https://dictionary.cambridge.org/dictionary/english/technology) as:
> the study and knowledge of the practical, especially industrial, use of scientific discoveries.

And [defines "accessibility"](https://dictionary.cambridge.org/dictionary/english/accessibility) as:
> the fact of being able to be reached or obtained easily; the quality of being able to be entered or used by everyone, including people who have a disability.

At first glance, these definitions look quite different, however they're linked by their real-world applications. The act of making something that everyone can use, or accessible, involves creating solutions using scientific discoveries, or via technology. Technology, with its nature of solving various problems that we encounter, then enables people to accomplish something that was previously impossible or difficult.

A high-level example I like is transportation. Anything that enables humans to traverse great distances and oceans enables access to regions of the world that would otherwise be out-of-reach. Unless a genetic mutation suddenly gives us the ability to fly or walk on water, overseas travel would be impossible without planes & boats.

Unfortunately, real-world applications of transportation systems often leave much to be desired, with [broken lifts](https://www.bbc.co.uk/news/articles/cly3jgypzvdo) and [damaged wheelchairs](https://tcf.org/content/report/trips-not-taken-money-not-made-inaccessible-air-travel-hurts-disabled-travelers-and-airlines-alike/) being part-and-parcel of the travel experience.
## How does this apply to websites?
I love the internet. We're able to connect with so much from the comfort of our own homes. It encompasses knowledge on every topic under the sun, a near-unlimited amount of entertainment, communication with people all around the world and more. The internet is such a valuable resource, and I believe it must be available to as many people as humanly possible.

We create the world we want to live in, and I want to live in a world that recognises that disabilities are disabling, and that tries its very best to work to reduce barriers of entry for as many people as possible. Since my area-of-expertise is frontend web development, my goal is to improve as many websites as I can, and empower you to do the same.

As developers and designers, we're responsible for the interfaces we create and curate, and this responsibility must include accessibility. We're already part-way there with mobile-responsiveness being a baked in expectation for websites, especially since [half of the world browses the web via a mobile device](https://www.statista.com/statistics/277125/share-of-website-traffic-coming-from-mobile-devices/). Cross-browser support is often a requirement, with tools like [Browserstack](https://www.browserstack.com/) used to enable testing on platform-specific browsers. Why wouldn't you take it further and include assistive devices amongst the list of peripherals and software you support?

If your immediate answer is something along the lines of "disabled people aren't my website's target audience," or "I don't know anyone that uses a screenreader," please consider that if someone using an assistive device cannot use your website, they will not use your website. You cannot know how someone will interact with your website, unless you make it available to them.
## A challenge for you
### For developers
- Reject that pull request (PR) that uses a `<div>` with a `click` handler.
- Downvote comments on Stack Overflow and similar forums that say anything close to "accessibility doesn't matter."
- Include accessibility in every PR (pull request) that you do. Don't bother waiting for a ticket, or for it to be added to a sprint. It never will. Sprinkle them into larger features or bug fixes where possible.

Bit by bit, line by line, suggestion by suggestion, eventually you'll have a marked improvement on your codebase and the websites that you're creating. Eventually, this might lead to incorporating accessibility in other areas of your job (as an example, ensuring that designs meet WCAG contrast requirements from the get go), but it will be better than what it was before.

### For designers
I'm not a designer, if you are, I would encourage you to research other methods on designing accessible interfaces. That being said, here's a few design changes I've had to run by designers before I could implement them:

- Test all colours used to ensure that they meet contrast requirements. Challenge brands undergoing designs or redesigns to use combinations of their colours that meet [WCAG contrast requirements](https://webaim.org/resources/contrastchecker/)
- Let the smallest font size be 12px (ideally 16px)
- Ensure that all interactive elements are at least 24 x 24px in size
- Use two methods of indicating interactivity for inline links (this is commonly colour and an underline)
- Reduce the amount of carousels
	- Ok maybe this suggestion is wishful thinking, but [carousels really are awful](https://thegood.com/insights/ecommerce-image-carousels/)

## Where do I start?
Here's a list of improvements I've suggested in PRs, and/or implemented myself in various codebases. Feel free to do more research on anything listed below, this is a quick-and-dirty checklist for low-hanging fruit:
- Links must always use `<a>`, instead of any element with Javascript powering the redirection
- Headings must be sequential; use CSS classes to manage styling
	- e.g. If you need `h4` styling after a `<h2>` element, then use `<h3 class="h4">heading</h3>`
- Ensure interactive icons have accessible text (e.g. `<span class="visually-hidden"></span>` or `aria-label=""`)
- Add `aria-hidden="true"` to all SVG elements

## How do I find the time?
Working in Agile environments, time estimates are the be-all-end-all for development related tasks. Understandably, getting dedicated time for accessibility audits and implementing fixes is quite tricky. 

My solution to that is to just do it anyways.

I touched on this earlier, but suggesting improvements to other developers in PRs, and creating PRs with semi-related accessibility fixes is how I started really pushing for (and eventually contributed to) company-wide accessibility standards at [We Make Websites](https://www.wemakewebsites.com/) (now [BORN Group](https://www.borngroup.com/)). My small suggestions like header order, removing/including certain ARIA attributes, adding `aria-hidden="true"` to SVG elements are lost in a sea of commit messages, change requests and approvals. But, they exist and their impacts were quite real. These eventually grew to changing approaches to product card structure, Figma designs meeting WCAG contrast requirements by default, and documentation for developers on specific methods of the accessible implementation of various features.

## Conclusion
Technology enables access and access is granted via technology. Accessibility and technology are intertwined by the nature to solve problems that people encounter, with the biggest difference being that accessibility shines a spotlight on disabilities.

As frontend developers, we are responsible for building websites that people can or cannot use. I simply believe that **all** people should be able to use the websites I create. 

If you've been able to make a website you work on more accessible, I'd love to hear from you! Feel free to send me an email at hello@georgiabains.com.
