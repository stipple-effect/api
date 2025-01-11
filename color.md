[`< API`](README.md)

# `color` extension

This API inherits the `color` type from the [*DeltaScript* base language![](./assets/external.png)](https://github.com/jbunke/deltascript/blob/master/docs/color-sl.md) and extends it in the ways described below.

## Properties

These definitions use the arbitrary `color` object `C` as the caller.

### Hue (`hue`)
```js
C.hue -> float
```
Returns the hue of a color `C` as a `float` ranging from 0.0 to 1.0. Since hue is a circular/angular property, a hue of 0.0 and a hue of 1.0 are identical. A hue of 0.0 is conventionally assigned to red ([`#ff0000`![](./assets/external.png)](https://en.wikipedia.org/wiki/Red), for example), while green is assigned to 1/3 (120°) and blue is assigned to 2/3 (240°).

**Read more:**

* [Defining hue in terms of RGB![](./assets/external.png)](https://en.wikipedia.org/wiki/Hue#Defining_hue_in_terms_of_RGB)

### Saturation (`sat`)
```js
C.sat -> float
```
Returns the [saturation![](./assets/external.png)](https://en.wikipedia.org/wiki/Colorfulness#Saturation) of a color `C` as a `float` ranging from 0.0 to 1.0.

### Value (`val`)
```js
C.val -> float
```
Returns the [value![](./assets/external.png)](https://en.wikipedia.org/wiki/HSL_and_HSV) of a color `C` as a `float` ranging from 0.0 to 1.0.
