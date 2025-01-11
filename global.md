[`< API`](README.md)

# Global namespace (`$SE`)

[`< API`](README.md)

The global namespace for this API is `$SE`. Most API functions that are not called on an object are called on the global namespace.

---

## Constants

Constants are bound to primitive data values like `int` or `bool`. Thus, they can technically be avoided and replaced by their literal values. However, using constants makes scripts more __*readable*__ and __*maintainable*__, and most importantly ensures that scripts do not break if the value assigned to a constant changes in a future update.

### Scope constants

These constants are used to specify a [scope](../docs/scope.md) for program operations like [palettization](../docs/palettization.md), for example.

```js
$SE.PROJECT = 0         // The entire project
$SE.LAYER = 1           // All cels on the currently selected layer
$SE.FRAME = 2           // All cels at the currently frame index
$SE.CEL = 3             // The cel on the current layer at the current frame index
```

### Save type constants

These constants are used to specify a [save type](../docs/save.md) for a [`save_config`](./save_config.md) object. Save types are essentially the type of file that the `save_config` object will save projects as, though there are multiple save types that save projects to the same type of file, albeit differently.

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

### ![](https://raw.githubusercontent.com/stipple-effect/stipple-effect/master/res/icons/new_project.png) `new_project`
1.  ```js
    $SE.new_project(int w, int h, bool open_in_se) -> project
    ```
    Creates a new project with a canvas size specified by `w` x `h` pixels and returns its reference.
    
    If `open_in_se` is `true`, the new project is opened in Stipple Effect and set as the active project.

    **Fails:**

    Any of the following will cause the function not to execute:

    * `w < 0`
    * `w > 1920`
    * `h < 0`
    * `h > 1080`

2.  ```js
    $SE.new_project(int w, int h) -> project
    ```
    Equivalent to `$SE.new_project(w, h, true)`
3.  ```js
    $SE.new_project(int w, int h);
    ```
    Like (2), but does not return the reference to the newly created project.

## Miscellaneous functions

### `new_save_config`
```js
$SE.new_save_config(string[] folder, string filename, int save_type) -> save_config
```
Instantiates a new `save_config` object with the parent folder path `folder`, base file name `filename`, and save type specified by the `int` enumeration value `save_type`.

**Throws:**

Any of the following will result in runtime errors:

* An invalid `save_type` value
* If `folder` is empty
* If `folder` is not a valid directory in the file system
* If `filename` is `""` or contains any of the following characters:
    ```js
    { '/', '\\', ':', '*', '?', '"', '<', '>', '|', '{', '}' }
    ```

**Read more:**
* [Save type constants](global.md/#save-type-constants)

### `read_script`
```js
$SE.read_script(string filepath) -> script
```
Reads, builds and returns a Stipple Effect child script from `filepath`.

**Throws:**

Any of the following will result in runtime errors:

* If the interpreter cannot read a file at `filepath`
* If the file at `filepath` cannot be compiled into a Stipple Effect script due to syntax errors

Script execution will terminate if the child script fails its semantic error check.

**Read more:**
* [Child scripts in the documentation](../docs/child-scripts.md)

### `transform`
1.  ```js
    $SE.transform(project source, script transformer, bool open_in_se, bool run_per_layer) -> project
    ```
    Transforms the contents of the project `source` into a new project with the preview script `transformer`. `source` is not modified by this operation.

    The flag `open_in_se` will open the resultant project in Stipple Effect and set it as the active project.

    The flag `run_per_layer` will apply `transformer` to the contents of each layer of `source`, as opposed to applying `transformer` to the flattened contents of `source`. This way, `run_per_layer` preserves the layers of `source`.

    **Note:**

    Depending on `transformer`, the flattened contents of a project created with `transform()` with the `run_per_layer` flag *may not match* the contents of a project created without the `run_per_layer` flag.
2.  ```js
    $SE.transform(project source, script transformer) -> project
    ```
    Equivalent to `$SE.transform(source, transformer, true, false)`

    Runs (1) with the `open_in_se` flag set to `true` and the `run_per_layer` flag set to `false`.

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

### ![](https://raw.githubusercontent.com/stipple-effect/stipple-effect/master/res/icons/new_palette.png) `new_pal`
```js
$SE.new_pal(color{} cs, string name);
```
Creates a new palette in Stipple Effect from the set of colors `cs` with the name `name`.

### `hsv`
1.  ```js
    $SE.hsv(float h, float s, float v, int a) -> color
    ```
    Returns a color built from its hue, saturation, value and alpha components. Unlike `rgba()`, which takes as arguments integer values ranging from 0 to 255, each of the HSV component arguments (`h`, `s` and `v`) is a float ranging from 0.0 to 1.0. `a`, however, is still an integer ranging from 0 to 255.

    **Throws:**

    Any of the following will result in a runtime exception:

    * For any `comp` of `h`, `s`, `v`; `comp < 0.0`
    * For any `comp` of `h`, `s`, `v`; `comp > 1.0`
    * `a > 255`
    * `a < 0`
2.  ```js
    $SE.hsv(float h, float s, float v) -> color
    ```
    Equivalent to `$SE.hsv(h, s, v, 255)`

## Outline functions

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

**Fails:** 

Any of the following will cause the function not to execute:

* `#|side_mask != 8`
* For any `i`, `side_mask[i] < -10`
* For any `i`, `side_mask[i] > 10`

### ![](https://raw.githubusercontent.com/stipple-effect/stipple-effect/master/res/icons/outline.png) `outline`
```js
$SE.outline(int[]{} selection, int[] side_mask) -> int[]{}
```
Returns the outline of the initial selection `selection` when outlined with the side mask `side_mask`.

**Read more:**

* [Outlining algorithm in the source code![](./assets/external.png)](https://github.com/stipple-effect/stipple-effect/blob/master/src/com/jordanbunke/stipple_effect/selection/Outliner.java)

**Throws:**

Any of the following will result in runtime errors:

* `#|side_mask != 8`
* For any `i`, `side_mask[i] < -10`
* For any `i`, `side_mask[i] > 10`

### ![](https://raw.githubusercontent.com/stipple-effect/stipple-effect/master/res/icons/outline.png) `single_outline`
```js
$SE.single_outline(int[]{} selection, int border_px) -> int[]{}
```
Returns the outline of the initial selection `selection` when outlined with the single outline side mask with a border thickness of `border_px` pixels. A single outline outlines along the cardinal directional borders of the selection only.

**Throws:**

Any of the following will result in runtime errors:

* `border_px < -10`
* `border_px > 10`

### ![](https://raw.githubusercontent.com/stipple-effect/stipple-effect/master/res/icons/outline.png) `double_outline`
```js
$SE.double_outline(int[]{} selection, int border_px) -> int[]{}
```
Returns the outline of the initial selection `selection` when outlined with the double outline side mask with a border thickness of `border_px` pixels. A double outline outlines along the cardinal directional borders of the selection as well as the diagonal borders.

**Throws:**

Any of the following will result in runtime errors:

* `border_px < -10`
* `border_px > 10`

## Tool functions

### ![](https://raw.githubusercontent.com/stipple-effect/stipple-effect/master/res/icons/wand.png) `wand`
```js
$SE.wand(image img, int x, int y, float tolerance, bool global, bool diag) -> int[]{}
```
Returns a set of ordered pairs that represent the pixel coordinates of the result of a wand tool operation on the image `img`.

**Parameters:**

* `img` - Image upon which the wand operation is performed
* `(x, y)` - Initial position from which the wand searches; equivalent to the pixel that is clicked when the wand tool is used from within the Stipple Effect UI
* `tolerance` - value from 0.0 (exact match) to 1.0 (maximally permissive) that determines how permissive of differences in color the wand is between the initial pixel and pixels being processed for inclusion
* `global` (flag)
  * if `true`, wand searches the entire canvas irrespective of adjacency
  * if `false`, the wand iteratively searches from among the frontier of pixels adjacent to selection inclusions
* `diag` (flag)
  * if `true`, adjacency is defined as cardinal adjacency + diagonal adjacency
  * if `false`, pixels must be cardinally adjacent in order to be considered

**Read more:**

* [`wand` and `fill` search algorithm implementation![](./assets/external.png)](https://github.com/stipple-effect/stipple-effect/blob/master/src/com/jordanbunke/stipple_effect/tools/ToolThatSearches.java)

### ![](https://raw.githubusercontent.com/stipple-effect/stipple-effect/master/res/icons/fill.png) `fill`
```js
$SE.fill(image img, color c, int x, int y, float tolerance, bool global, bool diag) -> image
```
<!-- TODO - rewrite -->

Returns the resultant image of a fill operation applied to the image `img`. `fill()` performs the exact same search and computation as [`wand()`](#wand). However, instead of returning a selection as a `int[]{}`, `fill()` takes that selection and sets every pixel in that selection to the color `c` in `img`.

### ![](https://raw.githubusercontent.com/stipple-effect/stipple-effect/master/res/icons/fill.png) `fill_selection`
1.  ```js
    $SE.fill_selection(image img, color c, int[]{} selection) -> image
    ```
    Returns the resultant image of a fill operation applied to the image `img` where all the pixels in `selection` are set to `c` in `img`.
2.  ```js
    $SE.fill_selection(image img, color c) -> image
    ```
    Returns the resultant image of a fill operation applied to the image `img` where all the pixels in the current selection in the active Stipple Effect project are set to `c` in `img`.
