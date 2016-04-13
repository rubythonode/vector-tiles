# [mapbox.com/developers/vector-tiles](https://mapbox.com/developers/vector-tiles)

This is a home for all vector tile documentation on mapbox.com.

* What are vector tiles
* `mapbox-streets` & `mapbox-terrain` documentation
* Vector tile specification interactive
* More?

### Contribute

Uses Jekyll to generate pages.

**Generate docs**

```bash
jekyll serve --watch
# listen at http://localhost:4000/developers/vector-tiles/
```

All pages are in the `_posts/` directory and use the `_layouts/docs.html` layout, which is an extension of the `www.mapbox.com` default layout, which is syncronized through [sync-templates](https://github.com/mapbox/sync-templates/) to keep all major styles in sync.