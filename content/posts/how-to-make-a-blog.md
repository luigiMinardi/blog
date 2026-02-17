+++
title="How to make a blog"
description="How can you make a blog just like this one using Hugo and Congo"
summary="How can you make a blog just like this one using Hugo and Congo"
date="2026-02-17"
tags=["any", "hugo", "congo", "markdown"]
categories=["programming"]
+++

This is an opinionated resume of [Congo Docs](https://jpanther.github.io/congo/docs/)
with some parts added or excluded based on what I found more or less useful. At
the end of this post you will have a similar blog as this one as of the time of
writing.

You will need `git` for version management and most deploy places will need it
to import (pull) your repository (repo).

You will need a `Github` account if you choose `Github Pages` as your deploy
method.

## Installation

I recommend managing `Hugo` and `Go` versions via [Mise](https://mise.jdx.dev/installing-mise.html)
if you're not good with CLI's you can use [Mise Versions](https://mise-versions.jdx.dev)
to browse the package you want to install via Mise.

Install [Hugo extended edition](https://gohugo.io/installation/) at version
`0.146.0` or later.
```sh
mise use hugo-extended@latest
```

Install [Go](https://go.dev/dl/) at version `1.13` or later.
```sh
mise use go@latest
```

### Create a new site

This will create a directory `blog` with the default Hugo directories.
```sh
hugo new site blog
```

### Add Congo theme

#### Initialize Hugo modules
Hugo is written in `go`, and the command is using `go mod` behind the scenes to
manage your dependencies.

Technically you can put whatever name you want after `init`, that is your project
name.

Since `go` do not have a package manager you need the `init` to be the same as
the address to your `git` repository where the code is hosted. This allow people
to import and run your code on their machines if they want (for example to help
you translate a blog post to another language or fix typos).

I'm assuming `GitHub` here as I will show how to deploy on `GitHub Pages` as
it's my current config. If you host your code on `Codeberg`, `Gitlab` or any
other place change to the URL that fits you.

On GitHub you will need to pass your `username` matching the GitHub one and
`repo-name` is the name of the repository you created on GitHub for the blog.
```sh
hugo mod init github.com/<username>/<repo-name>
```
#### Add the theme in your config
Navigate to `config/_default/module.toml` (create the file/directories if
needed) and paste this:
```toml
[[imports]]
path = "github.com/jpanther/congo/v2"
```
then [run the server](#running-the-server-locally)
#### Updating the theme

Clear the cache and update all modules:
```sh
hugo mod clean
```
```sh
hugo mod get -u
```
Sometimes it doesn't get you up to the latest version, in those cases if you
want to update the theme to a new version you do so by running the following
command (replace `@v2.13.0` with the current latest version, you can check it
on the [Changelog](https://github.com/jpanther/congo/blob/dev/CHANGELOG.md)).
```sh
hugo mod get github.com/jpanther/congo/v2@v2.13.0
```

Then clean the `go.sum` file:
```sh
hugo mod tidy
```

### Running the server locally

```sh
hugo server
```

#### Running with drafts enabled
`-D` (`--buildDrafts`) include draft content for the local server I always
prefer using it.
```sh
hugo server -D
```
#### Running on your local IP
If you want to check the blog in your phone or other screen sizes you can run
the server on your local IP and access it anywhere in your local network.
```sh
hugo server -D --bind 192.168.1.123 --baseURL http://192.168.1.123
```
#### Running with clear cache
This is useful when changing frequently some files that are cached and do not
load without you killing the server and running again or when ever by restarting
the server and refreshing the page you still don't see the changes you added.

- `--disableFastRender` do full render on changes (slower)
- `--gc` (garbage collector) remove unused cache files after the build
- `--ignoreCache` to make sure you won't use the `cache` directory
- `--noHTTPCache` prevent HTTP caching
- `--forceSyncStatic` copy all files when `static` changes
- `-w` (`--watch`) watch file system changes and recreate the server as needed
```sh
hugo server -D --disableFastRender --gc --ignoreCache --noHTTPCache --forceSyncStatic -w
```

## Configuring Congo
Delete the default `hugo.toml` in the root of the project, then you will create
the following files under `config/_default`.

### config/_default
```sh
config/_default/
├─ hugo.toml
├─ languages.en.toml
├─ markup.toml
├─ menus.toml
├─ module.toml # you already have this one
└─ params.toml
```

You can copy the content of all but the `module.toml` one from the
[Congo GitHub](https://github.com/jpanther/congo/tree/stable/config/_default)
to get latest the default config.

Bellow you can see some available configurations that I found useful, adjust
them per your need and with your data.

For the full list of options and documentation check the [Congo Configuration](https://jpanther.github.io/congo/docs/configuration/)
docs.

#### hugo.toml
[Hugo privacy docs](https://gohugo.io/configuration/privacy/)
```toml
# -- Site Configuration --
# Refer to the theme docs for more details about each of these parameters.
# https://jpanther.github.io/congo/docs/getting-started/

baseURL = "https://your_domain.com/"
title= "My Blog Title"

defaultContentLanguage = "en"

enableRobotsTXT = true
summaryLength = 1

[pagination]
  pagerSize = 10

[outputs]
  home = ["HTML", "RSS", "JSON"]

[privacy]
  [privacy.vimeo]
    enableDNT = true
  [privacy.x]
    enableDNT = true
  [privacy.youTube]
    privacyEnhanced = true
  [privacy.googleAnalytics]
    respectDoNotTrack = true

[services]
  [services.x]
    disableInlineCSS = true
```
#### languages.en.toml
```toml
languageCode = "en"
languageName = "English"
languageDirection = "ltr"
weight = 1

title = "Congo"
copyright = "© Custom Copyright text 2026"

[params]
  dateFormat = "2 January 2006"

  mainSections = ["section1", "section2"] # "posts", "projects" or any taxonomy you set and want it to be tracked by Congo/Hugo
  description = "My awesome website"

[params.author]
  name = "Your name here"
  image = "img/author.jpg"
  headline = "I'm only human"
  bio = "A little bit about you"
  links = [
     { email = "mailto:hello@your_domain.com" },
     { link = "https://link-to-some-website.com/" },
     { amazon = "https://www.amazon.com/hz/wishlist/ls/wishlist-id" },
     { apple = "https://www.apple.com" },
     { blogger = "https://username.blogspot.com/" },
     { codepen = "https://codepen.io/username" },
     { dev = "https://dev.to/username" },
     { discord = "https://discord.gg/invitecode" },
     { dribbble = "https://dribbble.com/username" },
     { facebook = "https://facebook.com/username" },
     { flickr = "https://www.flickr.com/photos/username/" },
     { foursquare = "https://foursquare.com/username" },
     { github = "https://github.com/username" },
     { gitlab = "https://gitlab.com/username" },
     { google = "https://www.google.com/" },
     { google-scholar = "https://scholar.google.com/citations?user=user-id" },
     { hashnode = "https://username.hashnode.dev" },
     { instagram = "https://instagram.com/username" },
     { keybase = "https://keybase.io/username" },
     { kickstarter = "https://www.kickstarter.com/profile/username" },
     { kofi = "https://ko-fi.com/username" },
     { lastfm = "https://lastfm.com/user/username" },
     { linkedin = "https://linkedin.com/in/username" },
     { mastodon = "https://mastodon.instance/@username" },
     { medium = "https://medium.com/username" },
     { mendeley = "https://www.mendeley.com/" },
     { microsoft = "https://www.microsoft.com/" },
     { orcid = "https://orcid.org/userid" },
     { patreon = "https://www.patreon.com/username" },
     { pinterest = "https://pinterest.com/username" },
     { reddit = "https://reddit.com/user/username" },
     { researchgate = "https://www.researchgate.net/profile/username" },
     { slack = "https://workspace.url/team/userid" },
     { snapchat = "https://snapchat.com/add/username" },
     { soundcloud = "https://soundcloud.com/username" },
     { stack-overflow = "https://stackoverflow.com/users/userid/username" },
     { steam = "https://steamcommunity.com/profiles/userid" },
     { telegram = "https://t.me/username" },
     { threads = "https://threads.net/@username" },
     { tiktok = "https://tiktok.com/@username" },
     { tumblr = "https://username.tumblr.com" },
     { twitch = "https://twitch.tv/username" },
     { whatsapp = "https://wa.me/phone-number" },
     { x-twitter = "https://twitter.com/username" },
     { youtube = "https://youtube.com/username" },
     { xing = "https://xing.com/profile/username" },
   ]
```
#### markup.toml
```toml
# -- Markup --
# These settings are required for the theme to function.

[goldmark]
[goldmark.renderer]
  unsafe = true
[goldmark.extensions]
[goldmark.extensions.passthrough]
  enable = true
[goldmark.extensions.passthrough.delimiters]
  block = [['\[', '\]'], ['$$', '$$']]
  inline = [['\(', '\)']]

[highlight]
  noClasses = false

[tableOfContents]
  startLevel = 2
  endLevel = 4
```
#### menus.en.toml
```toml
# -- Main Menu --
# The main menu is displayed in the header at the top of the page.
# Acceptable parameters are name, pageRef, page, url, title, weight.
#
# The simplest menu configuration is to provide:
#   name = The name to be displayed for this menu link
#   pageRef = The identifier of the page or section to link to
#
# By default the menu is ordered alphabetically. This can be
# overridden by providing a weight value. The menu will then be
# ordered by weight from lowest to highest.

[[main]]
  name = "Blog"
  pageRef = "posts"
  weight = 10

[[main]]
  name = "Categories"
  pageRef = "categories"
  weight = 20

[[main]]
  name = "Tags"
  pageRef = "tags"
  weight = 30

[[main]]
  identifier = "search"
  weight = 99
  [main.params]
    action = "search"

[[main]]
  identifier = "locale"
  weight = 100
  [main.params]
    action = "locale"

# -- Footer Menu --
# The footer menu is displayed at the bottom of the page, just before
# the copyright notice. Configure as per the main menu above.

[[footer]]
   name = "Tags"
   pageRef = "tags"
   weight = 10
```
#### params.toml
This do not cover [Advanced Customisations](https://jpanther.github.io/congo/docs/advanced-customisation/#colour-schemes).
```toml
# -- Theme Options --
# These options control how the theme functions and allow you to
# customise the display of your website.
#
# Refer to the theme docs for more details about each of these parameters.
# https://jpanther.github.io/congo/docs/configuration/#theme-parameters

colorScheme = "congo" # valid options: congo (default), avocado, cherry, fire, ocean, sapphire and slate. 
defaultAppearance = "dark" # valid options: light or dark
autoSwitchAppearance = false
description = "The blog from You"

defaultThemeColor = "#FFFFFF"

enableSearch = true
enableCodeCopy = true
enableImageLazyLoading = true
enableImageWebp = true

# robots = ""
fingerprintAlgorithm = "sha256"

[header]
  layout = "basic" # valid options: basic, hamburger, hybrid, custom
  logo = "img/logo.jpg"
  logoDark = "img/dark-logo.jpg"
  showTitle = true

[footer]
  showCopyright = true
  showThemeAttribution = true
  showAppearanceSwitcher = true
  showScrollToTop = true

[homepage]
  layout = "profile" # valid options: page, profile, custom
  showRecent = false
  recentLimit = 5

[article]
  showDate = true
  showDateUpdated = true
  showAuthor = true
  showBreadcrumbs = true
  showDraftLabel = true
  showEdit = true
  editURL = "https://github.com/username/repo/"
  editAppendPath = true
  showHeadingAnchors = true
  showPagination = true
  invertPagination = false
  showReadingTime = true
  showTableOfContents = true
  showTaxonomies = true
  showWordCount = true
  showComments = true
  sharingLinks = ["facebook", "x-twitter", "mastodon", "pinterest", "reddit", "linkedin", "email", "threads", "telegram", "line", "weibo", "xing", "bluesky"]

[list]
  showBreadcrumbs = true
  showSummary = true
  showTableOfContents = true
  showTaxonomies = true
  groupByYear = true
  paginationWidth = 1

[sitemap]
  excludedKinds = ["taxonomy", "term"]

[taxonomy]
  showTermCount = true

[fathomAnalytics]
  # site = "ABC12345"

[plausibleAnalytics]
  # domain = "blog.yoursite.com"
  # event = ""
  # script = ""

[umamiAnalytics]
#  site = "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"
#  region = "eu"  # can be either "eu" or "us"

[verification]
  # google = ""
  # bing = ""
  # pinterest = ""
  # yandex = ""
```

## Organizing Content
```sh
.
├── assets
│   └── img
│       └── author.jpg
├── config
│   └── _default
└── content
    ├── _index.md
    ├── about.md
    └── posts
        ├── _index.md
        ├── first-post.md
        └── another-post
            ├── aardvark.jpg
            └── index.md
```
Within the `content` directory, normal article pages are named `index.md` and
Hugo call those pages `Leaf Pages`, while list pages are named `_index.md` and
list the leaf pages under the same directory and subdirectories (as long as the
subdirectory is not a new list page, e.g `content/posts/subcategory/_index.md`
creates a new list page and thus separate the articles from inside the
subcategory from the list of articles on the posts directory.).

Any assets that go along with the article should be placed in a sub-directory
alongside the index file (like shown on the `another-post` example) or placed
under `assets` and linked directly or via the [Front Matter](#front-matter)
depending on the purpose of the asset and if it's used globally or only in the
article.

This means that `posts/_index.md` will be a list page that you can access
through `yoursite.com/posts/` and it will list `first-post` and `another-post`
as the posts available.

### Feature, cover and thumbnail images
```sh
.
└── content
    └── posts
        ├── _index.md
        └── first-post
            ├── cover.jpg
            ├── index.md
            └── thumb.jpg
```
Those are the three types of supported images to display on article listings,
for details check the [Congo docs on it](https://jpanther.github.io/congo/docs/getting-started/#feature-cover-and-thumbnail-images).

The gist of it is the image filename need to say `feature`, `cover` or `thumb`
to be used as either of them.

Feature is used as both `cover` and `thumb`, and also as metadata when shared
on Discord, Twitter (x), Facebook, etc.

Thumbs are cropped and resized as `4:3` ratio by default.

Covers are resized to fit their content by default, any ratio allowed.

### Taxonomies
If you want to customize your taxonomies check the [related Congo docs](https://jpanther.github.io/congo/docs/getting-started/#taxonomies)
and [Hugo docs](https://gohugo.io/content-management/taxonomies/) on it.

### Front Matter
This is the metadata you add on the top part of your markdown file like this
one for this blog post:
```toml
+++
title="How to make a blog"
description="How can you make a blog just like this one using Hugo and Congo"
summary="How can you make a blog just like this one using Hugo and Congo"
date="2026-02-12"
tags=["any", "hugo", "congo", "markdown"]
categories=["programming"]
+++
```
You only need to specify any parameter in your front matter when you want to
override the default from the theme base configuration.

For the full list of possible parameters check [Congo Front Matter docs](https://jpanther.github.io/congo/docs/front-matter/).

On section pages (`_index.md`) you can add `cascade` settings that affect that
entire section.
```toml
+++
title="Projects"
description="Projects list"
[[cascade]]
  showReadingTime=false
+++
This section contains all my current projects.
```

#### External links
You can add links to external posts by creating a normal article page (without
`_`) and setting `externalUrl` to the Front Matter of the theme and configuring
`build` so that Hugo don't try to create a page out of this file.
```toml
+++
title="My Medium post"
date="2022-01-25"
externalUrl="https://medium.com/"
summary="I wrote a post on Medium."
showReadingTime=false
[[build]]
  render=false
  list="local"
+++
```

You can generate a file with the above Front Matter via:
```sh
hugo new -k external posts/my-post.md
```

### Shortcodes
While writing your posts you might want some extra functionality that don't
exist on basic markdown, Hugo provide a [few shortcodes](https://gohugo.io/content-management/shortcodes/)
for that and Congo provide [even more](https://jpanther.github.io/congo/docs/shortcodes/)
for you to use.

Those give you things like charts, KaTex (Tex math notation), mermaid
(diagrams), buttons, etc.

### Comments
To add comments refer to [Congo Docs](https://jpanther.github.io/congo/docs/partials/#comments).

I'm still investigating myself what is the better way to do it, for now I'm
looking at [Giscus](https://giscus.app) and [GraphComment](https://www.graphcomment.com/en).

There are a few other options [recommended by Hugo](https://gohugo.io/content-management/comments/#alternatives).

# Hosting & Deployment

Follow the [GitHub Pages Congo Docs](https://jpanther.github.io/congo/docs/hosting-deployment/#github-pages)
to host on GH Pages, or check the other options they suggest.

## Extra stuff

### Extending head, footer or article link
If you want to add custom html to your `<head>`, `<footer>` or insert
additional code after article links you can do so by modifying
`layouts/partials/extend-head.html`, `layouts/partials/extend-footer.html` or
`layouts/partials/extend-article-link.html` respectively.

More info at [Congo Partials Docs](https://jpanther.github.io/congo/docs/partials/#extensions).

### Creating custom layouts
Congo gives you freedom to create [your custom layouts](https://jpanther.github.io/congo/docs/content-examples/#custom-layouts)
by following the [Hugo docs](https://gohugo.io/templates/introduction/).

You can also override the theme layouts, creating a
`layouts/_default/single.html` allows you to overwrite the default layout of
leaf pages.

### Default Keyboard Shortcuts from Congo
- `/` Can be used to search in the website
- `Esc` to quit search
- `Down Arrow` to move down in the results list
- `Up Arrow` to move up in the results list
