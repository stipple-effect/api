[`< API`](README.md)

# `$Graphics`

The `$Graphics` namespace houses graphics utilities for processing images and colors.

---

## Constants

### Light direction constants

These constants are common presets to be used as directions for directional lights.

```js
$Graphics.DL_TOP = [ 0.0, 1.0, 1.0 ]            // From the top
$Graphics.DL_LEFT = [ -1.0, 0.0, 1.0 ]          // From the left
$Graphics.DL_RIGHT = [ 1.0, 0.0, 1.0 ]          // From the right
$Graphics.DL_BOTTOM = [ 0.0, -1.0, 1.0 ]        // From the bottom
$Graphics.DL_TL = [ -1.0, 1.0, 1.0 ]            // From the top-left
$Graphics.DL_TR = [ 1.0, 1.0, 1.0 ]             // From the top-right
$Graphics.DL_BL = [ -1.0, -1.0, 1.0 ]           // From the bottom-left
$Graphics.DL_BR = [ 1.0, -1.0, 1.0 ]            // From the bottom-right
$Graphics.DL_DIRECT = [ 0.0, 0.0, 1.0 ]         // Frontlit
```

**Read more:**
* [`light`](./light.md)
* [Directional light constructor](#dir_light)

## Functions

### `dir_light`
```js
$Graphics.dir_light(float luminosity, color c, float[] direction) -> light
```

Creates and returns a directional [`light`](./light.md) with a luminosity `luminosity`, a base color `c`, and a direction specified by the vector `direction`.

A directional light, as opposed to a point light, shines with a non-dimming luminosity/intensity from a particular direction. It does not originate at any particular position.

**Note:**

`light` objects are mutable. Arguments `luminosity`, `c`, and `direction` passed to the constructor can be overridden by using the mutator methods of `light`.

**Read more:**
* [Light direction constants](#light-direction-constants)

### `gen_lookup`
```js
$Graphics.gen_lookup(image source, bool dim) -> image
```

Takes an image `source` and generates a corresponding lookup image where every non-transparent pixel in `source` is assigned a unique opaque RGB color. The flag `dim` determines whether the lookup will have vertical or horizontal striping.

**Read more:**
* [Lookup generation algorithm implementation![](./assets/external.png)](https://github.com/jbunke/delta-time/blob/master/sprite/src/com/jordanbunke/delta_time/sprite/UVMapping.java#L85)
* [Dimension constants](./global.md#dimension-constants)

### `hsv`
1.  ```js
    $Graphics.hsv(float h, float s, float v, int a) -> color
    ```
    Returns a color built from its hue, saturation, value and alpha components. Unlike `rgba()`, which takes as arguments integer values ranging from 0 to 255, each of the HSV component arguments (`h`, `s` and `v`) is a float ranging from 0.0 to 1.0. `a`, however, is still an integer ranging from 0 to 255.

    **Throws:**

    Any of the following will result in a runtime exception:

    * For any `comp` of `h`, `s`, `v`; `comp < 0.0`
    * For any `comp` of `h`, `s`, `v`; `comp > 1.0`
    * `a > 255`
    * `a < 0`
2.  ```js
    $Graphics.hsv(float h, float s, float v) -> color
    ```
    Equivalent to `$Graphics.hsv(h, s, v, 255)`

### `lerp_color`
```js
$Graphics.lerp_color(color a, color b, float t) -> color
```

Returns the resultant `color` of a linear interpolation operation performed on colors `a` and `b`.

* If `t <= 0.0`, returns `a`
* If `t >= 1.0`, returns `b`
* Otherwise (`0.0 < t < 1.0`), returns color specified by `a + (Δ * t)` where `Δ = b - a`

### `lighting`
```js
$Graphics.lighting(image texture, image normal, light<> lights) -> image
```

Sequentially applies a list of lights `lights` to `texture` by referencing the surface normal data provided by `normal`, and returns the lit image.

If `texture` and `normal` do not have the same dimensions, returns `texture`.

### `point_light`
```js
$Graphics.point_light(float luminosity, color c, float radius, int x, int y, float z) -> light
```

Creates and returns a point [`light`](./light.md) with a source luminosity `luminosity`, a base color `c`, a radius `radius`, a source pixel position specified by `x` and `y`, and a relative source Z-axis position specified by `z`.

A `z` value of `0.0` means the light is level along the Z-axis with an image being illuminated. A positive `z` value means the light is **in front** of an illuminated image, while a negative `z` value means the light is **behind** an illuminated image.

A point light, as opposed to a directional light, originates at a specified point and shines from its source position with a linearly dimming luminosity up to a distance specified by its radius.

**Note:**

`light` objects are mutable. Arguments `luminosity`, `c`, `radius`, `x`, `y`, and `z` passed to the constructor can be overridden by using the mutator methods of `light`.

### `uv_mapping`
```js
$Graphics.uv_mapping(image texture, image map, image animation) -> image
```

**Parameters:**
* `texture` - a color texture
* `map` - a lookup map corresponding to the shape and dimensions of `texture` where every non-transparent pixel should have a unique color
* `animation` - a specification for an animation using the colors in `map`

**Returns:**

If `texture` and `map` do not have the same dimensions, returns `animation`. 

Otherwise, returns the following image:

* Initializes a blank image with the same dimensions as `animation`
* For every non-transparent pixel at position `(ax, ay)` in `animation`...
  * checks if the color `c` sampled at that pixel is present in `map`
  * If it is...
    * assigns the first (and ideally only) pixel instance of `c` as `(mx, my)`
    * sets position `(ax, ay)` of the output image to the color of the pixel at `(mx, my)` in `texture`
  * If it isn't...
    * sets position `(ax, ay)` of the output image to `c`
  

**Read more:**
* [UV mapping algorithm implementation![](./assets/external.png)](https://github.com/jbunke/delta-time/blob/master/sprite/src/com/jordanbunke/delta_time/sprite/UVMapping.java#L40)
* [`gen_lookup()`](#gen_lookup) - generating a naive lookup map for a `texture`
