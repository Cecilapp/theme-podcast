# Cecil component theme: Podcast

Podcast component theme for [Cecil](https://cecil.app).

## Installation

```bash
composer require cecil/theme-podcast
```

> Or [download the latest archive](https://github.com/Cecilapp/theme-podcast/releases/latest/) and uncompress its content in `themes/podcast`.

## Usage

Add `podcast` in the `themes` section of your `config.yml`:

```yaml
theme:
  - podcast
```

Add podcast details:

```yaml
podcast:
  author: Cecil
  owner:
    name: Cecil
    email: contact@cecil.app
  image: cover.png
  categories:
    - Technology
  explicit: "false"
  type: episodic
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

Add episodes in `episodes`'s section with this required informations:

```yaml
---
title: "Episode X"
date: YYYY-MM-DD
episode:
  file: /episode-X.mp3
  season: 0
  number: X
  type: full
  explicit: "false"
  block: no
---
```

Add the HTML player to your episode's template:

```twig
{% include 'partials/audioplayer.html.twig' %}
```
