# Appendix A: Legacy Functions
These functions will be deprecated in the near future.

## `setEndscreen(endscreenType)`

Provides a mechanism to set the `endscreenType` after the initial creation. Available options: `replay, rcommCounterScreen, rcommScreen`. The default `endscreenType` is `replay`. If any `recommendations` are set, the default `endscreenType` will be `rcommScreen`.

## `setRecommendations(recommendations)`

Provides a mechanism to set the `recommendations` after the initial creation. The parameter `recommendations` is expected to be an array of content resource objects (see [Recommendation Model](#recommendation-model.md)).

### Recommendation Model<a name="recommendation-model"></a>

| property | default | type | description | example  
|----------|---------|------|-------------|---------
| title | `''` | String | Title of the recommendation | `'Another Episode'` |
| description | `''` | String | Short description | `'In this episode a new character will be introduced.'` |
| home_url | `''` | String | Target url of recommendation item | `'http://home-url/foo'` 
| theme_url | `''` | String | Target channel of recommendation if existing | `'http://theme-url/foo'` |
| duration | `''` | String | Duration content length | `'30.08'` |
| thumbnail | `''` | Array | Thumbnail picture url | `[{url:'/dynamic/thumbnail'}]` |
