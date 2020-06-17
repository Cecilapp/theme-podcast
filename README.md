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
  image: /images/cecil-logo.png
  categories:
    - Society & Culture
    - History
```

Add episodes in `episodes`'s section with this required informations:

```yaml
---
episode:
  file: /audio/test.mp3
---
```

Add the HTML player to your episode's template:

```twig
{% include 'partials/audioplayer.html.twig' %}
```
