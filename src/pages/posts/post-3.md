---
title: 'Creating a layout component'
pubDate: 2025/07/22
description: 'Creating BaseLayer.astro to re-use my layout across my pages.'
author: 'tk'
image:
    url: 'https://docs.astro.build/assets/rose.webp'
    alt: 'The Astro logo on a dark background with a pink glow.'
tags: ["astro", "blogging", "learning in public"]
---
# Third Blog Post
Today, I refactored my code to prevent my page from repeatedly rendering Astro components on each page.

Instead of the repeated HTML for Index, About and Blog, I moved to this new BaseLayout file. This BaseLayout file was then imported into each of these pages instead and utilised through the "<BaseLayout>" tags on each page instead.

Any HTML specific to that page could still be included by adding it between the <BaseLayout> tags instead, this was the same for any <style> tags and styling added to specific pages. (Note - this also required adding slot tags in BaseLayout to inject the content).

Finally, I passed the pageTitle value from each of the pages to the layout component. I then changed the BaseLayout component again to receive the page title through Astro.props instead of defining it as a constant. This would have been an issue because the BaseLayout component is just the Index page copied and pasted and therefore would have had a static title. 