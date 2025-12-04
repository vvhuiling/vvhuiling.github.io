# Personal Website

This is my personal website and blog, built with [Jekyll](https://jekyllrb.com/) and hosted on [GitHub Pages](https://pages.github.com/).

## About This Site

This website is built using the [Millennial](https://github.com/LeNPaul/Millennial) Jekyll theme, a minimalist theme designed for personal blogs and publications.

## Features

* Compatible with GitHub Pages
* Clean and minimalist design
* Responsive layout
* Support for blog posts and static pages
* [Google Analytics](https://www.google.com/analytics/) support
* Commenting support powered by [Disqus](https://disqus.com/)
* Optimized for search engines
* LaTeX support through [MathJax](https://www.mathjax.org/)
* Syntax highlighting for code blocks

## Local Development

To run this site locally:

1. Install Jekyll and dependencies:

   ```bash
   bundle install
   ```

2. Start the Jekyll server:

   ```bash
   bundle exec jekyll serve
   ```

3. Open your browser and visit `http://localhost:4000`

## Configuration

Main configuration files:

* `_config.yml` - Site build settings and metadata
* `_data/settings.yml` - Theme settings, menu, and social media links

## Adding New Posts

To add a new blog post, create a new file in the `_posts` directory following the naming convention:

```text
YYYY-MM-DD-post-title.md
```

Each post should include YAML front matter:

```yaml
---
layout: post
title: "Your Post Title"
author: "Your Name"
categories: [category]
tags: [tag1, tag2]
image: image-name.jpg
---
```

## License

This website content is licensed under the [MIT License](LICENSE.md).

## Credits

This website uses the **Millennial** Jekyll theme created by [Paul Le](https://github.com/LeNPaul).

### Theme Creator

#### Paul Le

* [www.lenpaul.com](http://lenpaul.com)
* [Twitter](https://twitter.com/paululele)
* [GitHub](https://github.com/LeNPaul)

### Theme Contributors

* [b-morawiec](https://github.com/b-morawiec)
* [JainVikas](https://github.com/JainVikas)
* [mschaeffner](https://github.com/mschaeffner)
* [cfe316](https://github.com/cfe316)
* [JeremyGonzales](https://github.com/JeremyGonzales)

### Icons + Resources

* [Font Awesome](http://fontawesome.io/) - Icons
* [Death to Stock](https://deathtothestockphoto.com/) - Demo Images

### Built With

* [Jekyll](https://jekyllrb.com/) - Static site generator
* [GitHub Pages](https://pages.github.com/) - Hosting platform

---

Thank you to all the contributors and creators who made this theme possible!
