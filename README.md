# Cecil component theme: Podcast

> The _Podcast_ component theme for [Cecil](https://cecil.app) provide templates to publish an audio show on the web.

- a RSS output for the `episodes` section (with a style sheet)
- a HTML audio player with resume feature and [Media Session API](https://developer.mozilla.org/docs/Web/API/Media_Session_API) support
- a generic cover image

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

Add podcast configuration details:

```yaml
podcast:
  author: Cecil
  owner:
    name: Cecil
    email: contact@cecil.app
  image: cover.png
  categories:
    - Technology
  type: episodic
  explicit: no
  block: no
  subscribe:
    - name: apple
      url: https://podcasts.apple.com/fr/podcast/staticast/idXXXXXXXXXX
      enabled: true
    - name: google
      url: https://podcasts.google.com/feed/XXXXXXXXXX
      enabled: true
    - name: spotify
      url: https://open.spotify.com/show/XXXXXXXXXX
      enabled: true
```

Add episode in `episodes`'s section with data (in the [front matter](https://cecil.app/documentation/content/#front-matter)) and description:

```yaml
---
title: "Episode X"
date: YYYY-MM-DD
episode:
  file: /episode-X.mp3
  season: 0    # optional
  number: X    # optional
  type: full   # optional
  explicit: no # optional
  block: no    # optional
---
Episode description.
```

Add the HTML player to your episode's template:

```twig
{% include 'partials/audioplayer.html.twig' %}
```
