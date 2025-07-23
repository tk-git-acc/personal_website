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

## Automatically creating new pages for tags
I edited [tag].astro to automatically check for unique tags in the blog posts, rather than having to add them statically each time a new umique tag is added.

This was done by creating an array of unique tags using JS/TypeScript using:

`const uniqueTags = [...new Set(allPosts.map((post: any) => post.frontmatter.tags).flat())];`

I then edited the existing params to reflect this change.

Finally, I added the line below:

`{posts.map((post: any) => <BlogPost post={post} />)}`

This loops through the post array and creates a <BlogPost /> component for each.

## Building a tag index page
Having built the dynamically created tag pages, I now needed to build a tag index page.

I created a new page `src/pages/tags/index.astro`, imported my BaseLayout and set the page title.

I then gave the page access to all posts and tags using:

`const allPosts = Object.values(import.meta.glob('../posts/*.md', { eager: true }));`

and 

`const tags = [...new Set(allPosts.map((post: any) => post.frontmatter.tags).flat())];`

I then created a list of all tags, added links and styling.

Finally, I added the new page to my navigation bar component.