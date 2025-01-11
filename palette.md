[`< API`](README.md)

# `palette`

`palette` objects created in scripts are internally represented by the [`Palette`![](./assets/external.png)](https://github.com/stipple-effect/stipple-effect/blob/master/src/com/jordanbunke/stipple_effect/palette/Palette.java) class from the *Stipple Effect* source code.

---

## Functions

For an arbitrary `palette` object named `P`, functions of the form `P.func_name(parameters) -> return_type` are __*value-returning functions*__, while functions of the form `P.func_name(parameters);` are __*void functions*__, which perform an action but return nothing.

### `colors`
```js
P.colors() -> color{}
```
Returns a set of the colors in the palette `P`.

### `included`
```js
P.included() -> color{}
```
Returns a set of the colors marked as "included" in the palette `P`.

### ![](https://raw.githubusercontent.com/stipple-effect/stipple-effect/master/res/icons/add_color_to_palette.png) `add_color`
```js
P.add_color(color c);
```
Adds the color `c` to the palette `P`.

**Fails** if `P.colors().has(c)`

### ![](https://raw.githubusercontent.com/stipple-effect/stipple-effect/master/res/icons/remove_color_from_palette.png) `remove_color`
```js
P.remove_color(color c);
```
Removes the color `c` from the palette `P` if `P` contains `c`.

### ![](https://raw.githubusercontent.com/stipple-effect/stipple-effect/master/res/icons/move_color_left_in_palette.png) `move_color_left`
```js
P.move_color_left(color c);
```
Swaps the color `c` with the color to its left in the palette `P` if `c` is not the "leftmost" color in `P`.

**Fails** if `!P.colors().has(c)`

### ![](https://raw.githubusercontent.com/stipple-effect/stipple-effect/master/res/icons/move_color_right_in_palette.png) `move_color_right`
```js
P.move_color_right(color c);
```
Swaps the color `c` with the color to its right in the palette `P` if `c` is not the "rightmost" color in `P`.

**Fails** if `!P.colors().has(c)`
