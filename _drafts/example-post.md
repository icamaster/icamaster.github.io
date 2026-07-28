---
# Copy this file to _posts/YYYY-MM-DD-my-slug.md to publish it.
# Files in _drafts/ are ignored unless you run `jekyll serve --drafts`.
title: "An example post"
date: 2026-01-01
# Shown on the homepage / blog cards:
image: /images/randomPic.jpg
tag: "Personal Project"
blurb: >-
  One or two sentences describing the post. This is what appears under the title on the homepage card. If omitted, the start of the post is used.
---

Write normally in Markdown. **Bold**, _italic_, [links](https://example.com), lists, and tables all work.

## A heading

Plain Markdown images are centered automatically and capped at 65% width, the same proportion the older hand-written project pages use:

![Some alt text](/images/randomPic.jpg)

When you want a caption, use the figure include instead:

{% include figure.html
   src="/images/PINTRY/PCBfront.jpg"
   alt="Pintry-X2 PCB Front"
   caption="Pintry-X2 PCB Front" %}

Pass `width="40%"` to the include to override the default size.

## Code

Fenced blocks are syntax highlighted:

```c
int main(void) {
    return 0;
}
```

## Publishing it

1. Move this file to `_posts/2026-08-01-my-slug.md` (the date prefix is required).
2. Add `- post: my-slug` to `_data/homepage.yml`, at whatever position on the homepage you want it to occupy.

The post shows up on `/blog/` automatically; the homepage entry is the only manual step, which is what keeps the homepage ordering under your control.
