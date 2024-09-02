<!-- Proofread and update for 1.2.0 -->
<!-- TODO:
    * $SE.read_script(string) -> script
    * $SE.new_save_config(string[], string, int) -> save_config
    * $SE.transform(project, script, bool, bool) -> project
    * $SE.transform(project, script) -> project
-->

# Global namespace (`$SE`)

[`< API`](README.md)

The global namespace for this API is `$SE`. All Stipple Effect functions that are not called on an object are called on the global namespace.

---

## Constants

Constants are bound to primitive data values like `int` or `bool`. Thus, they can technically be avoided and replaced by their literal values. However, using constants makes scripts more __*readable*__ and __*maintainable*__, and most importantly ensures that scripts do not break if the value assigned to a constant changes in a future update.

### Scope constants

These constants are used to specify a [scope](https://github.com/jbunke/se-docs/blob/master/scope.md) for program operations like [palettization](https://github.com/jbunke/se-docs/blob/master/palettization.md), for example.

```js
$SE.PROJECT = 0         // The entire project
$SE.LAYER = 1           // All cels on the currently selected layer
$SE.FRAME = 2           // All cels at the currently frame index
$SE.CEL = 3             // The cel on the current layer at the current frame index
```

### Save type constants

These constants are used to specify a [save type](https://github.com/jbunke/se-docs/blob/master/scope.md) for a [`save_config`](save_config.md) object. Save types are essentially the type of file that the `save_config` object will save projects as, though there are multiple save types that save projects to the same type of file, albeit differently.

```js
$SE.NATIVE = 0          // The native file type (.stip)
$SE.PNG_SHEET = 1       // The project as a single PNG image/sprite sheet
$SE.PNG_SEPARATE = 2    // Separate PNG images for each frame of the project
$SE.GIF = 3             // An animated GIF
$SE.MP4 = 4             // MP4 video
```

### Dimension constants

```js
$SE.HORZ = true         // Horizontal sequencing order; L to R, T to B
$SE.VERT = false        // Vertical sequencing order; T to B, L to R
```

---

Functions of the form `$SE.func_name(parameters) -> return_type` are __*value-returning functions*__, while functions of the form `$SE.func_name(parameters);` are __*void functions*__, which perform an action but return nothing.

## Project functions

### `get_projects`
```js
$SE.get_projects() -> project[]
```
Returns an array of the projects that are currently opened in Stipple Effect.

### `get_project`
```js
$SE.get_project() -> project
```
Returns the current active project in Stipple Effect.

### ![](https://raw.githubusercontent.com/jbunke/stipple-effect/master/res/icons/new_project.png) `new_project`
1.  ```js
    $SE.new_project(int w, int h, bool open_in_se) -> project
    ```
    Creates a new project with a canvas size specified by `w` x `h` pixels and returns its reference.
    
    If `open_in_se` is `true`, the new project is opened in Stipple Effect and set as the active project.

    **Constraints:** `0 < w <= 1920 && 0 < h <= 1080`
2.  ```js
    $SE.new_project(int w, int h) -> project
    ```
    Equivalent to `$SE.new_project(w, h, true)`
3.  ```js
    $SE.new_project(int w, int h);
    ```
    Like (2), but does not return the reference to the newly created project.

## Color functions

### `get_primary`
```js
$SE.get_primary() -> color
```
Returns the current Stipple Effect system primary color.

### `set_primary`
```js
$SE.set_primary(color c);
```
Sets the Stipple Effect primary color to `c`.

### `get_secondary`
```js
$SE.get_secondary() -> color
```
Returns the current Stipple Effect system secondary color.

### `set_secondary`
```js
$SE.set_secondary(color c);
```
Sets the Stipple Effect secondary color to `c`.

### `get_pal`
```js
$SE.get_pal() -> palette
```
Returns the currently selected Stipple Effect system palette.

### `has_pal`
```js
$SE.has_pal() -> bool
```
Returns `true` if there is at least one palette in Stipple Effect at the time of the call, `false` otherwise.

### ![](https://raw.githubusercontent.com/jbunke/stipple-effect/master/res/icons/new_palette.png) `new_pal`
```js
$SE.new_pal(color{} cs, string name);
```
Creates a new palette in Stipple Effect from the set of colors `cs` with the name `name`.

### `hsv`
1.  ```js
    $SE.hsv(float h, float s, float v, int a) -> color
    ```
    Returns a color built from its hue, saturation, value and alpha components. Unlike `rgba()`, which takes as arguments integer values ranging from 0 to 255, each of the HSV component arguments (`h`, `s` and `v`) is a float ranging from 0.0 to 1.0. `a`, however, is still an integer ranging from 0 to 255.
2.  ```js
    $SE.hsv(float h, float s, float v) -> color
    ```
    Returns a color built from its hue, saturation and value components.

    `$SE.hsv(h, s, v) <=> $SE.hsv(h, s, v, 255)`

## Outline functions

### ![](https://raw.githubusercontent.com/jbunke/stipple-effect/master/res/icons/outline.png) `outline`
```js
$SE.outline(int[]{} selection, int[] side_mask) -> int[]{}
```
Returns the outline of the initial selection `selection` when outlined with the side mask `side_mask`. The outlining algorithm can be found [here](https://github.com/jbunke/stipple-effect/blob/master/src/com/jordanbunke/stipple_effect/selection/Outliner.java).

<!-- TODO: add constraints -->

### ![](https://raw.githubusercontent.com/jbunke/stipple-effect/master/res/icons/outline.png) `single_outline`
```js
$SE.single_outline(int[]{} selection, int border_px) -> int[]{}
```
Returns the outline of the initial selection `selection` when outlined with the single outline side mask with a border thickness of `border_px` pixels. A single outline outlines along the cardinal directional borders of the selection only.

### ![](https://raw.githubusercontent.com/jbunke/stipple-effect/master/res/icons/outline.png) `double_outline`
```js
$SE.double_outline(int[]{} selection, int border_px) -> int[]{}
```
Returns the outline of the initial selection `selection` when outlined with the double outline side mask with a border thickness of `border_px` pixels. A double outline outlines along the cardinal directional borders of the selection as well as the diagonal borders.

### `get_side_mask`
```js
$SE.get_side_mask() -> int[]
```
Returns the current system outline side mask. This is an eight-element integer array. The indices correspond to the following directions:
```js
0 = TOP 
1 = LEFT 
2 = RIGHT 
3 = BOTTOM 
4 = TL 
5 = TR 
6 = BL 
7 = BR
```

### `set_side_mask`
```js
$SE.set_side_mask(int[] side_mask);
```
Sets the Stipple Effect outline side mask to `side_mask`.

**Constraints:** `#|side_mask == 8`

## Tool functions

### ![](https://raw.githubusercontent.com/jbunke/stipple-effect/master/res/icons/wand.png) `wand`
```js
$SE.wand(image img, int x, int y, float tolerance, bool global, bool diag) -> int[]{}
```
Returns a set of arrays of two integers that represent the pixel coordinates of the result of a wand tool operation on the image `img`. `x` and `y` represent the initial target pixel of `img` that the operation is initiated from. `tolerance` is a value ranging from 0.0 (exact match) to 1.0 (trivial) that determines how tolerant the threshold of color similarity between the target pixel and any pixel to be included is. If `global` is true, the search algorithm searches the entire canvas irrespective of adjacency and includes all pixels that comply with the tolerance. If `global` is false, inclusions must be adjacent to the initial target pixel or at least one other inclusion. If `diag` is true, adjacency is defined as cardinal adjacency + diagonal adjacency. If `diag` is false, adjacency is simply defined as cardinal adjacency. For every `int[] coord` in the return set `int[]{}`, `coord[0]` is the pixel X coordinate and `coord[1]` is the pixel Y coordinate. The searching algorithm for `wand` and `fill` can be found [here](https://github.com/jbunke/stipple-effect/blob/master/src/com/jordanbunke/stipple_effect/tools/ToolThatSearches.java).

### ![](https://raw.githubusercontent.com/jbunke/stipple-effect/master/res/icons/fill.png) `fill`
```js
$SE.fill(image img, color c, int x, int y, float tolerance, bool global, bool diag) -> image
```
Returns the resultant image of a fill operation applied to the image `img`. `fill` performs the exact same search and computation as `wand`. However, instead of returning a selection as a `int[]{}`, `fill` takes that selection and sets every pixel in that selection to the color `c` in `img`.

### ![](https://raw.githubusercontent.com/jbunke/stipple-effect/master/res/icons/fill.png) `fill_selection`
1.  ```js
    $SE.fill_selection(image img, color c, int[]{} selection) -> image
    ```
    Returns the resultant image of a fill operation applied to the image `img` where all the pixels in `selection` are set to `c` in `img`.
2.  ```js
    $SE.fill_selection(image img, color c) -> image
    ```
    Returns the resultant image of a fill operation applied to the image `img` where all the pixels in the current selection in the active Stipple Effect project are set to `c` in `img`.
