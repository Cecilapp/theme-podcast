# Cecil component theme: Podcast

The _Podcast_ component theme for [Cecil](https://cecil.app) provide templates to publish an audio show on the web:

1. a RSS output for the `episodes` section (with a style sheet)
2. a HTML audio player with resume feature and [Media Session API](https://developer.mozilla.org/docs/Web/API/Media_Session_API) support

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
    name: Cecil
    email: contact@cecil.app
  image: cover.png
  author: Cecil
  categories:
    - Technology
  type: episodic
  explicit: no
  block: no
  newfeedurl: '' # optional, the URL of the new feed in case of hosting changement
```

Add an episode in `episodes` section with data (in the [front matter](https://cecil.app/documentation/content/#front-matter)) and description:

_1.md_:

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
Description and notes of the episode.
```

Add the HTML player to your episode's template:

```twig
{% include 'partials/audioplayer.html.twig' %}
```
