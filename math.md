# `$Math`

[`< API`](README.md)

The `$Math` namespace houses mathematical constants and functions that may be useful when writing scripts.

**Note:**

There are additional mathematical functions available in DeltaScript that are implemented as native functions. These include:
* `abs()` - [absolute value](https://en.wikipedia.org/wiki/Absolute_value)
* `min()`, `max()` - minimum/maximum of two numbers or of a collection
* `clamp(min, v, max)` - returns `min` if `v < min`, `max` if `v > max`, `v` otherwise

[**\[read more\]**](https://github.com/jbunke/deltascript) <!-- TODO - update link -->

---

## Constants

### `PI`
```js
$Math.PI
```
[Pi](https://en.wikipedia.org/wiki/Pi) represented as a `float`.

**Note:**

The `float` type in DeltaScript is actually implemented as a [double-precision floating point number](https://en.wikipedia.org/wiki/Double-precision_floating-point_format), and is internally mapped to Java's `double` primitive type.

[**\[`Double` wrapper class Java documentation\]**](https://docs.oracle.com/javase/8/docs/api/java/lang/Double.html)

---

## Functions

### `cos`
```js
$Math.cos(float rad) -> float
```
<!-- TODO -->

### `sin`
```js
$Math.sin(float rad) -> float
```
<!-- TODO -->

### `tan`
```js
$Math.tan(float rad) -> float
```
<!-- TODO -->

### `acos`
```js
$Math.acos(float ratio) -> float
```
<!-- TODO -->

### `asin`
```js
$Math.asin(float ratio) -> float
```
<!-- TODO -->

### `atan`
```js
$Math.atan(float ratio) -> float
```
<!-- TODO -->

### `sqrt`
```js
$Math.sqrt(float n) -> float
```
<!-- TODO -->

### `round`
```js
$Math.round(float n) -> float
```
<!-- TODO -->

### `floor`
```js
$Math.floor(float n) -> float
```
<!-- TODO -->

### `ceil`
```js
$Math.ceil(float n) -> float
```
<!-- TODO -->
