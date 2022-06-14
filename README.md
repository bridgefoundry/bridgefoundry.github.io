Bridge Foundry Web Site
=======================

This site is build with [Jeykll](https://jekyllrb.com/) and hosted on
[GitHub Pages](https://pages.github.com/) -- pushing the main branch will
update the website.


## Adding a blog post

1. Check out this repo with `git clone` to your local computer.
2. Create a file in the `_posts` directory. The format of the file name is
important! It should be `YYYY-MM-DD-first-few-words-or-desc-of-post.md`. The
date is the date that the blog post should appear to have been published on.
3. Add the following Jekyll "front matter" to the top of your new markdown file:
```
---
layout: post
title: This is the Title of Your Blog Post
tags: ready
---
```
4. On the next empty line, compose your post. You can use Markdown tags like `**bold**` or even raw HTML.
5. Follow the steps in the rest of this README for local previewing ("Local development") and deployment of your post.


## Local development

Install Ruby and then run:

```
gem install bundler
bundle
```

Note: the website integrates two other repos, which are each GitHub Pages
themselves. They're built individually and then automatically available under
the same domain.

If you want to make changes to those, work directly in these separate repos:

* [code of conduct](https://github.com/bridgefoundry/code-of-conduct)
* [workshop-map](https://github.com/bridgefoundry/workshop-map)

To run the site:

```
bundle exec jekyll serve
```

point your browser at: http://localhost:4000/


## Deploying the site

The website is automatically deployed upon changes merged to main. See [GitHub
documentation][docs] for more information.

[docs]: https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/about-github-pages-and-jekyll#building-your-site-locally
