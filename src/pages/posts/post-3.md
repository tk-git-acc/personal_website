---
layout: ../../layouts/MarkdownPostLayout.astro
title: 'Creating a layout component'
pubDate: 2025/07/22
description: 'Creating BaseLayout.astro & MarkdownPostLayout.astro to re-use my layouts across pages.'
author: 'tk'
image:
    url: 'https://docs.astro.build/assets/rose.webp'
    alt: 'The Astro logo on a dark background with a pink glow.'
tags: ["astro", "blogging", "HTML", "CSS", "JavaScript", "Personal Website"]
---
Today, I refactored my code to prevent repeatedly writing the same code across my various blog pages.

## Creating BaseLayout.astro

Instead of the repeated HTML for Index, About and Blog, I moved to this new BaseLayout file. This BaseLayout file was then imported into each of these pages and utilised through the "<BaseLayout>" tags on each page.

Any HTML specific to that page could still be included by adding it between the <BaseLayout> tags instead, this was the same for any <style> tags and styling added to specific pages.

Finally, I passed the pageTitle value from each of the pages to the layout component. I then changed the BaseLayout component again to receive the page title through Astro.props instead of defining it as a constant. 

The reasoning behind this is that I encountered an issue because the BaseLayout component is just the Index page copied and pasted and therefore would have had a static title. 

## Creating MarkdownPostLayout.astro

I added a layout specifically for blog posts called MardownPostLayout.astro.

This allowed me to remove repetitive code from the blog posts, as well as utilising the frontmatter for more dynamic and efficient content. 

This meant that I could take the e.g. date, author from the frontmatter and automatically put this in each blog post rather than typing it out each time.

I also then was able to apply the styles from global.css to my blog posts.

## Bugs

I found a bug following applying the MarkdownPostLayout.astro & global.css files to my blog posts.

I first noticed this when opening the site from a mobile view, and found that the content had huge margins on either side.

I realised that the meta viewport tag wasn't applying correctly. This was because the tag was in my BaseLayout file but not my MarkdownPostLayout file.

Once I added the tag here, the site displayed correctly on mobile.