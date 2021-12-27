# Ok-ish Blog Hugo Theme

An ok-ish blog theme based on [Vanilla](https://vanillaframework.io/). The theme
is responsive and supports multi-language mode, multiple authors, and [a few
more](#features). It's suitable for all types of blog posts.

![Screenshot of the
theme](https://raw.githubusercontent.com/kongdivin/hugo-theme-okayish-blog/master/images/screenshot.png)

## Features

* Support [I18n](https://gohugo.io/content-management/multilingual/)
* Support [Taxonomies](https://gohugo.io/content-management/taxonomies/)
* Optimized for accessibility and SEO
* Google `site:` Search
* Google Analytics
* Share links (Facebook, Twitter, and LinkedIn)
* Disqus Comments
* Provide meta tags for [Open Graph](https://ogp.me/), [Twitter
    Card](https://developer.twitter.com/en/docs/tweets/optimize-with-cards/overview/abouts-cards),
    and [Schema.org](https://schema.org/)

## Getting Started

> I assume that you already have a Hugo site project. If not, you can create one
> by following [Quick Start](https://gohugo.io/getting-started/quick-start/).

To use the theme, add it to your site's theme directory:

```sh
git submodule add https://github.com/kongdivin/hugo-theme-okayish-blog.git themes/hugo-theme-okayish-blog
```

Then tell Hugo to use `hugo-theme-okayish-blog` by adding/updating the following
in `config.toml`

```toml
# File: config.toml

theme = "hugo-theme-okayish-blog"
```

### Cloning an existing repository

If you have an existing repository that was setup with the steps above, you have
to pull in the theme submodule after cloning your repository using the following
command:

```sh
git submodule update --init
```

## Usage

Head over to [Content Managment](https://gohugo.io/content-management/) to learn
more how to manage your content.

### Configurations

```toml
# File: config.toml

baseURL = "https://example.com"
languageCode = "en-us"
defaultContentLanguage = "en-us"
title = "Your site's title"
copyright = "© 2021 Title"
theme = "hugo-theme-okayish-blog"

# Provide this id to enable Google Analytics
googleAnalytics = "UA-xxxxxxxxx-x"

# Provide the shortname to enable Disqus comments
disqusShortname = "ok-ish-blog"

[params]
# These will be used for OpenGraph, Twitter Card and Schema.org
description = "Your site's description"
keywords = ["some", "keywords", "for", "your", "site"]
images = ["/images/banner.png"]

# This is the number of terms within a taxonomy per page
termsPaginate = 50
# Enable/disable share links (Facebook, Twitter and LinkedIn)
shareLinksEnabled = true
# Enable/disable Google Analytics in local server
gaLocalEnabled = false

[taxonomies]
category = "categories"
tag = "tags"

# Add `author` under `[taxonomies]` as below
# so that you can provide metadata for each author
#
# See: https://gohugo.io/content-management/taxonomies/#add-custom-metadata-to-a-taxonomy-term
author = "authors"

# Add menu items to the navigation bar as below.
# N.B. Use identifiers as the keys for translations.
[menu]

[[menu.main]]
identifier = "authors"
name = "Authors"
url = "/authors"

[[menu.main]]
identifier = "categories"
name = "Categories"
url = "/categories"

# For i18n support, add the language codes here 
# and provide translations in `i18n` folder. E.g., `i18n/en-US.toml`
[languages]

[languages.en-us]
languageName = "English (US)"

[languages.km-kh]
languageName = "ភាសាខ្មែរ"
```

These configurations are the main ones. For more, please check [Configure
Hugo](https://gohugo.io/getting-started/configuration/).

### Custom Home Page

The default homepage is showing the list of pages in the main sections. In case
you want a custom homepage, you can create `layouts/index.html`. For example,

```html
<!-- File: layouts/index.html -->

{{ define "main"}}
<h1>My New Home Page</h1>
{{ end }}
```

Since the theme is using Vanilla. You can use all its available components. See
its [docs](https://docs.vanillaframework.io/) for more details. Need
inspirations? There you go, https://vanillaframework.io/showcase.

### Custom Style

To provide a custom stylesheet, create `layouts/partials/head-extension.html` in
your site directory to override the one the theme's created. Then put the link
to your stylesheet in that file. For example,

```html
<!-- File: layouts/partials/head-extension.html -->

<link href={{ "css/custom.css" | absURL }} rel="stylesheet"><link>

<link href="https://fonts.googleapis.com/css?family=Hanuman:400,700|Inconsolata|Roboto:400,400i,700,700i&display=swap&subset=khmer" rel="stylesheet"><link>
```

N.B. The theme includes fonts here. You might want to copy the `<link>` over;
otherwise, the fonts will be default to Vanilla's default fonts ([Ubuntu
font](https://design.ubuntu.com/font/)).

## Contributing

If you spot any bugs, please use [Issue
Tracker](https://github.com/kongdivin/hugo-theme-okayish-blog/issues). Or if you
want to add a new feature directly, please create a new [Pull
Request](https://github.com/kongdivin/hugo-theme-okayish-blog/pulls).

## License

Licensed under [The MIT
License](https://github.com/kongdivin/hugo-theme-okayish-blog/blob/master/LICENSE).
