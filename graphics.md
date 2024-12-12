# `$Graphics`

[`< API`](README.md)

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

**Reading material:**
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

**Reading material:**
* [Light direction constants](#light-direction-constants)

### `gen_lookup`
```js
$Graphics.gen_lookup(image source, bool dim) -> image
```
<!-- TODO -->

**Reading material:**
* [Dimension constants](./global.md#dimension-constants)

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
<!-- TODO -->
