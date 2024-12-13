# `light`

[`< API`](README.md)

`light`'s correspondent type in the Stippe Effect source code is [`Light`](https://github.com/jbunke/stipple-effect/blob/master/src/com/jordanbunke/stipple_effect/scripting/util/Light.java).

---

## Functions

For an arbitrary `light` object named `L`, functions of the form `L.func_name(parameters) -> return_type` are __*value-returning functions*__, while functions of the form `L.func_name(parameters);` are __*void functions*__, which perform an action but return nothing.

### `is_point`
```js
L.is_point() -> bool
```
Returns `true` if `L` is a point light, `false` if `L` is a directional light.

### `get_luminosity`
```js
L.get_luminosity() -> float
```
Returns the luminosity of `L`.

### `set_luminosity`
```js
L.set_luminosity(float luminosity);
```
Sets the luminosity of `L` to `luminosity`.

### `get_color`
```js
L.get_color() -> color
```
Returns the base color of `L`.

### `set_color`
```js
L.set_color(color c);
```
Sets the base color of `L` to `c`.

### `get_radius`
```js
L.get_radius() -> float
```
Returns the radius of a point light `L`.

**Throws** a runtime error if `!L.is_point()`

### `set_radius`
```js
L.set_radius(float radius);
```
Sets the radius of a point light `L` to `radius`.

**Fails** if `!L.is_point()`

### `get_z`
```js
L.get_z() -> float
```
Returns the relative Z-axis position of a point light `L`.

**Throws** a runtime error if `!L.is_point()`

### `set_z`
```js
L.set_z(float z);
```
Sets the relative Z-axis position of a point light `L` to `z`.

**Fails** if `!L.is_point()`

### `get_position`
```js
L.get_position() -> int[]
```
Returns the pixel source position of a point light `L`.

**Throws** a runtime error if `!L.is_point()`

### `set_position`
```js
L.set_position(int[] position);
```
Sets the pixel source position of a point light `L` to `position`.

**Fails** if `!L.is_point()`

### `get_direction`
```js
L.get_direction() -> float[]
```
Returns the direction of a directional light `L`.

**Throws** a runtime error if `L.is_point()`

### `set_direction`
```js
L.set_direction(float[] direction);
```
Sets the direction of a directional light `L` to the 3-dimensional vector `direction`.

**Fails** if `L.is_point()`
