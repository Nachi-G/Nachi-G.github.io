# Nachiketa Gulati portfolio

This static site is ready to publish with GitHub Pages.

## Add project media

For each project, aim for three visual assets: a strong cover image or short video, one build/CAD photo, and one test/result clip.

1. Put files in `media/` using concise names, such as `rover-cover.jpg`, `rover-build.jpg`, and `rover-demo.mp4`.
2. In `index.html`, replace any matching media placeholder with one of the following:

```html
<img class="project-media" src="./media/rover-demo.gif" alt="Voice-controlled rover driving">
```

```html
<video class="project-media" controls muted playsinline poster="./media/rover-cover.jpg">
  <source src="./media/rover-demo.mp4" type="video/mp4">
</video>
```

Use a clear, specific `alt` description for every image. For the best initial load speed, use a compressed MP4 for video and a still image as its poster. The same three slots appear in the project detail view.

## Publish to GitHub Pages

Copy everything in this folder to the repository for `nachi-g.github.io`, commit, and push to the branch configured in **Settings → Pages**. GitHub Pages will serve `index.html` automatically.

No build step or framework is required.
