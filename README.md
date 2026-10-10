# Podcast component theme

The _Podcast_ component theme for [Cecil](https://cecil.app) provide templates to publish an audio show on the web:

1. a RSS output for the `episodes` section (with a style sheet)
2. a HTML audio player with resume feature and [Media Session API](https://developer.mozilla.org/docs/Web/API/Media_Session_API) support

**[Demo](https://cecilapp.github.io/theme-podcast/)**

## Installation

```bash
composer require cecil/theme-podcast
```

> Or [download the latest archive](https://github.com/Cecilapp/theme-podcast/releases/latest/) and uncompress its content in `themes/podcast`.

## Usage

Add `podcast` in the `theme` section of your `config.yml`:

```yaml
theme:
  - podcast
```

Add podcast configuration details in your `config.yml`:

```yaml
podcast:
  owner:
    name: Cecil               # optional, defaults to `author.name` (or `author`), then `title`
    email: contact@cecil.app  # optional, defaults to `author.email`
  image: cover.png            # square image (1400x1400 to 3000x3000), defaults to the theme's cover.png
  author: Cecil               # optional, defaults to owner name
  categories:                 # https://podcasters.apple.com/support/1691-apple-podcasts-categories
    - Technology
  type: episodic              # optional, "episodic" (default) or "serial"
  explicit: false             # optional, `true` or `false` (default)
  block: false                # optional, `true` to hide the show from podcast directories
  newfeedurl: ""              # optional, the URL of the new feed in case of hosting change
  player:
    links:
      download: false         # display a "Download file" link under the player
      open: false             # display a "Play in new window" link under the player
```

Enable the RSS output of the `episodes` section (by default Cecil only generates HTML and Atom for sections):

```yaml
output:
  pagetypeformats:
    section: [html, rss]
```

> Or only for the `episodes` section, in the front matter of `pages/episodes/index.md`: `output: [html, rss]`.

The feed is available at `/episodes/rss.xml`, with a style sheet to display it nicely in browsers.

Add a Markdown file in `episodes` section with data (in the [front matter](https://cecil.app/documentation/content/#front-matter)) and description:

_1.md_:

```yaml
---
title: "Episode X"
date: YYYY-MM-DD
episode:
  file: episode-X.mp3 # MP3 file in `assets/`
  image: episode-X.png # optional
  season: 0       # optional
  number: X       # optional
  type: full      # optional, "full", "trailer" or "bonus"
  explicit: false # optional
  block: false    # optional
---
Description and notes of the episode.
```

Add the HTML player to your episode's template:

```twig
{% include 'partials/audioplayer.html.twig' %}
```

The player resumes playback where the listener left off, updates the page title with the current time, and supports the media keys/lock screen controls (seek, previous and next episodes). Add `#autoplay` to an episode URL to start playing automatically.

## Internationalization

The theme is translated in French (`translations/messages.fr.yml`). You can override or add translations in your site's `translations/` directory.

## Demo

The [`demo/`](demo/) folder contains a bilingual website using the theme. To run it locally:

```bash
curl -LO https://cecil.app/cecil.phar
php demo/link.php # links the repository as `demo/themes/podcast`
php cecil.phar serve demo
```

## License

_Podcast_ is a free software distributed under the terms of the MIT license.
