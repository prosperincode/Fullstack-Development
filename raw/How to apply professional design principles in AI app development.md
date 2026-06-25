---
title: "How to apply professional design principles in AI app development"
source: "https://expo.dev/blog/how-to-apply-professional-design-principles-in-ai-app-development"
author:
published: 2026-06-23
created: 2026-06-25
description: "Vibe-coded apps all look the same. Here are eight design principles that will give you the vocabulary to critique AI output and ship something that stands out."
tags:
  - "clippings"
---
Building a simple app is easy now. But the gap between apps spawned by vibe coding tools and apps made by professionals is visibly obvious.

It doesn’t need to be.

In this blog we’ll share a structure that will help you ship apps that are visually compelling.

Of course we could give you the DIY method: *go take some screenshots of apps you think are beautifully designed, ask AI to deconstruct the design into actionable items, and start baking the same designs into your app*. There are countless tutorials, plugins, and resources out there to help you incorporate a reasonably nice design for your apps.

But that is not the best way to build something unique and visually impressive. To stand out in the crowded landscape of vibe coded apps you need polish.

Polish is when persistence and taste meet **the science of design**.

## The limitations of agentic design

Agents are getting good at very specific design tasks like assembling most design patterns and layouts, especially when templates and existing codebases are available. But they remain hard to steer. Because design is not code.

And yet, if you inspect your chat you’ll probably see AI crunching code trying to translate what you meant by “align button to the main container edges”. Agents don’t have eyes. They can only prepare the ingredients and toss them all in the pot. Sometimes the output is a disaster. And sometimes the output looks totally fine. We all know that there is more to a great soup.

## The science of design

Visual design is a science of applied abstraction. There are [so](https://www.amazon.com/Non-Designers-Design-Book-4th/dp/0133966151) [many](https://www.amazon.com/Designing-Visual-Interfaces-Communication-Techniques/dp/0133033899) [books](https://www.amazon.com/Universal-Principles-Completely-Updated-Expanded/dp/076037516X) [on](https://www.amazon.com/Visual-Display-Quantitative-Information/dp/1930824130) [the](https://www.amazon.com/Grid-systems-graphic-design-communication/dp/3721201450) [matter](https://www.amazon.com/Dieter-Rams-Principles-Good-Design/dp/3791387324). Design is not an art. [John Maeda (famous designer/technologist)](https://www.linkedin.com/in/johnmaeda/) said ”Design is a solution to a problem. Art is a question to a problem".

Since its beginning, design has followed a set of core principles that have been applied to many domains ever since….architecture, print, landscaping, drawing, industrial engineering, and many more including, software. The myth of “good design” is elusive, cryptic, and yet so tangible. *You know it when you see it.*

## A functional framework for designing apps with AI

What you’re going to read here is a list of the qualities people see when they “ *know it when they see it* ”. Everything that we perceive to be visually harmonious checks each of these boxes:

- **Contrast** makes elements distinguishable. Differences in size, color, weight, or shape create hierarchy and draw the eye to what matters most. Without contrast, everything competes equally and nothing stands out.
- **Hierarchy** guides the viewer through content in order of importance. Headlines come before body text, primary actions look different from secondary ones. Size, position, color, and weight all signal "look here first."
- **Alignment** creates order and connection. Elements that share an edge or axis feel related and intentional. Strong alignment is invisible but its absence looks sloppy immediately.
- **Proximity** groups related items and separates unrelated ones. White space between groups tells the eye what belongs together without needing borders or boxes.
- **Repetition** (or consistency) builds cohesion. Reusing colors, fonts, shapes, and spacing patterns makes a design feel unified and helps users learn the system quickly.
- **Balance** distributes visual weight across the composition. Symmetrical balance feels stable and formal; asymmetrical balance feels dynamic but still resolved. Either works; an unbalanced layout feels off.
- **White space** (negative space) gives content room to breathe. It's not empty, it's active, and it determines how premium, calm, or cluttered a design feels.
- **Unity** is the overall sense that every element belongs. It emerges when the other principles are working together; nothing feels arbitrary or out of place.

Think of these as a framework to critique and iterate with AI. Unfortunately, creating a simple skill like “ [visual-design.md](http://visual-design.md/) ” won’t cut it. Remember, AI has no eyes (yet) but you can provide it with a screenshot and ask it to critique and revise its output based on this checklist.

## Applying design principles to AI driven app design

Here is an example of two designs for the same app. V1 is the Claude Code output before feedback based on the principles above, and V2 is after feedback.

### Contrast

In V1 the black and white image from the first cards clashes tonally with the soft warm hero image. There are a lot of colors, sizes and no obvious high-contrast focal point leading my eyes to the navigation.

V2 uses contrast surgically. A single white "Book now" pill sits on a dark, atmospheric background. It’s the only thing that looks clickable, so that's where your eye lands. The orange "Home" indicator in the nav is warm and quiet rather than electric blue, so it signals state without stealing attention from the primary CTA above it.

### Hierarchy

In V1, the hierarchy is muddled: the wordmark, the tagline, the location, "Our Experiences," and the experience card title all fight for similar levels of attention.

V2 establishes a crisp three-tier hierarchy: (1) hero image + tagline + Book now, (2) "Experiences" section label, (3) individual cards with name and price. Your eye moves top-to-bottom in the order the business actually wants: atmosphere, conversion, then browse.

### Alignment

V1 makes no particular mistakes when it comes to alignment. For simple UI like this there is only one container with 2 lateral axis. Good job Claude! V2 keeps the same alignment structure.

### Proximity

In V1, the tagline and locations are crammed under the wordmark over the hero photography, Three pieces of information stacked tightly with little breathing room. Then there's a hard and tight cute leading into dense cards.

V2 separates concerns: the hero communicates brand and mood. Experience get pushed below which eases the transition into browsing mode.

### Repetition

V1 mixes a sans-serif wordmark, a different weight for body text, blue iconography, orange accent text, and a black-and-white photo treatment on the card. It reads like several design decisions made independently.

V2 creates a system: one typeface family, consistent rounded pill shapes, warm orange as the sole accent color, and full-color photography throughout.

### Balance

V1 is bottom-heavy and lopsided. It’s a giant text-dense card dominates the lower two-thirds, while the hero feels truncated. The eye sinks.

V2 uses asymmetrical balance well: the hero image takes commanding space at the top, the CTA acts as a visual fulcrum in the middle, and two horizontally-scrolling cards anchor the bottom without overwhelming it. Weight is distributed top-to-bottom with intention.

### White Space

This is the biggest upgrade. In V1, every pixel is working (except for that weird top offset). Text on photo, dense card stack, four-icon nav. It feels cluttered, which is the opposite of what a wellness brand should evoke.

V2 lets the design breathe. Negative space around the logo mark, around the CTA, between the section label and the cards. That space is the brand promise: restoration, calm, room to breath.

### Unity

V1 feels like a template that got content poured into it. V2 feels intentional. Every choice (the nighttime hero, the warm orange accent, the rounded pills, the horizontal card scroll, the consistent margins) reinforces the same idea: a quiet, premium, nature-based experience. Unity isn't a separate technique; it's what you get when the other seven principles agree with each other, which is exactly what's happening on the right.

## Beware of utilitarian AI design

Note that AI agents tend to be very utilitarian and focus on features leading to a sterile UX. I recommend that you consider the agent output as a simple base to expand upon. For example the initial booking UX was very bare and would be a lot more enticing with recaps of the booking throughout the checkout.

The danger of settling for the sterile AI design is that you won’t stand out. Not in this world where so many people are capable of shipping an app. You need some design nuance to distance your work from the homogenous mass of AI built apps.

Working on design with AI can be challenging. Art directing as a human is challenging too. These visual design principles are the vocabulary for this iterative conversation.

Try them out and let us know how it goes!