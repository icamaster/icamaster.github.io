# Introduction

My personal page based on [Start Bootstrap - 3 Col Portfolio](https://startbootstrap.com/template-overviews/3-col-portfolio/) and built with [Jekyll](https://jekyllrb.com/).

# Instructions

## Prerequisites

### Windows

Install latest 3.x **Ruby+Devkit** from [rubyinstaller.org/downloads](https://rubyinstaller.org/downloads/).

Avoid Ruby 4.x for now: `http_parser.rb` does not link against the GCC 16 toolchain it ships with. Ruby 3.4.x is known to work.

Keep the checkout somewhere short, e.g. `D:\projects\icamaster.github.io`, otherwise you might run into path length problems. 

### Linux

```bash
# Debian / Ubuntu
sudo apt install ruby-full build-essential

# Fedora
sudo dnf install ruby ruby-devel gcc make redhat-rpm-config
```

### macOS

```bash
xcode-select --install   # compiler
brew install ruby        # the system Ruby is too old
```

### Building on a new architecture

`Gemfile.lock` records which platforms it resolves for; it currently covers Windows (`x64-mingw-ucrt`) and 64-bit Linux (`x86_64-linux`, which is what CI uses). On anything else, add it once and commit the result:

```bash
bundle lock --add-platform aarch64-linux   # ARM Linux, e.g. a Raspberry Pi
bundle lock --add-platform arm64-darwin    # Apple Silicon
```

Without this, `bundle install` refuses to run with "your bundle only supports platforms ...".

## Running it locally

```
bundle install                            # once
bundle exec jekyll serve --livereload     # http://localhost:4000
```

Add `--drafts` to also render files in `_drafts/`.

To reproduce exactly what gets deployed, including production-only output such as analytics:

```
JEKYLL_ENV=production bundle exec jekyll build
```

## Writing a new article

1. Copy `_drafts/example-post.md` to `_posts/YYYY-MM-DD-my-slug.md` and write it in Markdown. The front matter fields `image`, `tag` and `blurb` are what the cards display (if added to the homepage).
2. It appears on `/blog/` automatically.
3. To put it on the homepage, add a line to `_data/homepage.yml` at the position you want it to occupy:

   ```yaml
   - post: my-slug
   ```

The homepage order is exactly the order of `_data/homepage.yml` and not sorted by date. External links and the older hand-written pages are listed in the same file with their fields spelled out inline.

For a centered image with a caption inside a post:

```
{% include figure.html src="/images/foo.jpg" alt="Alt text" caption="A caption" %}
```

## Layout

| Path | Description |
| ---- | --- |
| `_data/homepage.yml` | Ordered list of homepage cards |
| `_posts/` | Blog articles, in Markdown |
| `_drafts/` | Unpublished drafts, including the example template |
| `_layouts/`, `_includes/` | Page shell, nav, footer, card and figure partials |
| `projects/` | Older hand-written project pages, served unchanged |
| `vendor/`, `css/`, `images/` | Bootstrap/jQuery, styles and assets |
| `.github/workflows/jekyll.yml` | Builds and deploys the site on push |
