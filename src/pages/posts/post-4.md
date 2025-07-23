---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Dynamically displaying blog posts and creating pages"
author: "tk"
description: "Dynamically listing my blog posts, refactoring, and creating pages dynamically from blog post tags"
image:
    url: "https://docs.astro.build/default-og-image.png"
    alt: "The word astro against an illustration of planets and stars."
pubDate: 2025-07-23
tags: ["astro", "JavaScript", "TypeScript"]
---
## Dynamically rendering a list of all of my blog posts
This post shows up with my other blog posts, because `import.meta.glob()` is returning a list of all my posts in order to create my list.

## Refactoring my blog page
I refactored my blog page using a new BlogPost component, which handles the rendering for each post.

This allowed me to keep my code modular and make it easier to reuse the BlogPost component.

## Create tag pages
I created pages dynamically from the 'tags' from the frontmatter of my blog posts. 

This involved creating a new file 'src/pages/tags/[tag].astro' and using the getStaticPaths() function to return an array of page routes.

I added the props to the new file that allowed it to utilise the data from each blog post.

I then filtered the posts shown on each dynamically created tag page to only show the relevant posts.