---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Dynamically displaying my blog posts from my blog page"
author: "tk"
description: "Using JS / TypeScript to create a dynamic list of my blog posts from blog.astro."
image:
    url: "https://docs.astro.build/default-og-image.png"
    alt: "The word astro against an illustration of planets and stars."
pubDate: 2025-07-23
tags: ["astro", "JavaScript", "TypeScript"]
---
This post shows up with my other blog posts, because `import.meta.glob()` is returning a list of all my posts in order to create my list.

