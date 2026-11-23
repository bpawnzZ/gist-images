# gist-images

Shared image host for GitHub gists.

Gists render **every image file inside them** as a full-size preview block above the
markdown, and they have a ~600 KB per-page render budget. Hosting images here instead
keeps each gist a single small `.md` that renders cleanly.

## Layout

One folder per gist:

```
<gist-slug>/<descriptive-name>.jpg
```

Example: `e300-tires/pirelli-p7-as-plus-3.jpg`

## Reference from a gist

Use absolute raw URLs — a relative path in a gist is silently rewritten to an in-page
anchor and renders as a broken image.

```markdown
![Pirelli P7 AS Plus 3](https://raw.githubusercontent.com/bpawnzZ/gist-images/main/e300-tires/pirelli-p7-as-plus-3.jpg)
```

The repo must stay **public** — raw URLs from a private repo require an auth header and
render as broken images in a gist.

## Rules

- One folder per gist, folder name = the gist's slug.
- Existing folders are immutable history — don't overwrite an image a published gist
  points at; add a new filename.
- Keep images at display resolution. Anything over ~800 px wide is wasted bytes.
