[`< API`](README.md)

# `$Math`

The `$Math` namespace houses mathematical constants and functions that may be useful when writing scripts.

**Note:**

There are additional mathematical functions available in *DeltaScript* that are included as part of the [standard library![](./assets/external.png)](https://github.com/jbunke/deltascript/blob/master/docs/std-lib.md).

---

## Constants

### `PI`
```js
$Math.PI
```
[Pi![](./assets/external.png)](https://en.wikipedia.org/wiki/Pi) represented as a `float`.

**Note:**

The `float` type in DeltaScript is actually implemented as a [double-precision floating point number![](./assets/external.png)](https://en.wikipedia.org/wiki/Double-precision_floating-point_format), and is internally mapped to Java's `double` primitive type.

**Read more:**

* [`Double` wrapper class Java documentation![](./assets/external.png)](https://docs.oracle.com/javase/8/docs/api/java/lang/Double.html)

---

## Functions

### `cos`
```js
$Math.cos(float rad) -> float
```
Returns the cosine of an angle (expressed in radians) `rad`.

**Wraps** Java's [`Math.cos(double)`![](./assets/external.png)](https://docs.oracle.com/javase/8/docs/api/java/lang/Math.html#cos-double-) function

### `sin`
```js
$Math.sin(float rad) -> float
```
Returns the sine of an angle (expressed in radians) `rad`.

**Wraps** Java's [`Math.sin(double)`![](./assets/external.png)](https://docs.oracle.com/javase/8/docs/api/java/lang/Math.html#sin-double-) function

### `tan`
```js
$Math.tan(float rad) -> float
```
Returns the tangent of an angle (expressed in radians) `rad`.

**Wraps** Java's [`Math.tan(double)`![](./assets/external.png)](https://docs.oracle.com/javase/8/docs/api/java/lang/Math.html#tan-double-) function

### `acos`
```js
$Math.acos(float ratio) -> float
```
Returns the arc cosine of `ratio`.

**Wraps** Java's [`Math.acos(double)`![](./assets/external.png)](https://docs.oracle.com/javase/8/docs/api/java/lang/Math.html#acos-double-) function

### `asin`
```js
$Math.asin(float ratio) -> float
```
Returns the arc sine of `ratio`.

**Wraps** Java's [`Math.asin(double)`![](./assets/external.png)](https://docs.oracle.com/javase/8/docs/api/java/lang/Math.html#asin-double-) function

### `atan`
```js
$Math.atan(float ratio) -> float
```
Returns the arc tangent of `ratio`.

**Wraps** Java's [`Math.atan(double)`![](./assets/external.png)](https://docs.oracle.com/javase/8/docs/api/java/lang/Math.html#atan-double-) function

### `sqrt`
```js
$Math.sqrt(float n) -> float
```
Returns the square root of a value `n`.

**Wraps** Java's [`Math.sqrt(double)`![](./assets/external.png)](https://docs.oracle.com/javase/8/docs/api/java/lang/Math.html#sqrt-double-) function

### `round`
```js
$Math.round(float n) -> float
```
Returns the closest integer to `n`, expressed as a `float`.

### `floor`
```js
$Math.floor(float n) -> float
```
Returns the largest integer less than or equal to `n`, expressed as a `float`.

**Wraps** Java's [`Math.floor(double)`![](./assets/external.png)](https://docs.oracle.com/javase/8/docs/api/java/lang/Math.html#floor-double-) function

### `ceil`
```js
$Math.ceil(float n) -> float
```
Returns the smallest integer greater than or equal to `n`, expressed as a `float`.

**Wraps** Java's [`Math.ceil(double)`![](./assets/external.png)](https://docs.oracle.com/javase/8/docs/api/java/lang/Math.html#ceil-double-) function
