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

### 1. Install Ruby

Install the Ruby version listed in `.ruby-version` (currently 3.3.13). Ruby
must be built against **OpenSSL 3**, or the `eventmachine` gem will fail to
compile during `bundle install`. On macOS, install OpenSSL 3 with Homebrew first:

```
brew install openssl@3
```

Then install Ruby with your version manager:

* **rbenv / asdf / mise:** these use OpenSSL 3 automatically, e.g.
  `rbenv install 3.3.13`.
* **RVM:** pass the OpenSSL path explicitly:
  ```
  rvm install 3.3.13 --with-openssl-dir=$(brew --prefix openssl@3)
  ```
  RVM also reads `.ruby-gemset` and switches to a project gemset
  (`bridgefoundry-site`) when you `cd` into this folder.

Check that Ruby is using OpenSSL 3:

```
ruby -v                                         # 3.3.13
ruby -ropenssl -e 'puts OpenSSL::OPENSSL_VERSION'   # OpenSSL 3.x
```

### 2. Install gems

```
gem install bundler
bundle install
```

Note: the website integrates two other repos, which are each GitHub Pages
themselves. They're built individually and then automatically available under
the same domain.

If you want to make changes to those, work directly in these separate repos:

* [code of conduct](https://github.com/bridgefoundry/code-of-conduct)
* [workshop-map](https://github.com/bridgefoundry/workshop-map)

### 3. Run the site

```
bundle exec jekyll serve
```

point your browser at: http://localhost:4000/

These warnings during the build are expected and can be ignored:

* `GitHub Metadata: No GitHub API authentication could be found`
* `To use retry middleware with Faraday v2.0+, install faraday-retry gem`

### Troubleshooting

* **`eventmachine` fails to build** (for example `Undefined symbols ...
  _SSL_get1_peer_certificate`): your Ruby was built against a different
  OpenSSL than the one `eventmachine` finds. Reinstall Ruby against OpenSSL 3
  as described above, then run `bundle install` again.
* **`cannot load such file -- openssl`** when running `gem install`: Ruby was
  built without OpenSSL. Reinstall it as described above.


## Deploying the site

The website is automatically deployed upon changes merged to main. See [GitHub
documentation][docs] for more information.

[docs]: https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/about-github-pages-and-jekyll#building-your-site-locally
