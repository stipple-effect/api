# `project`

[`< API`](README.md)

`project`'s correspondent type in the Stippe Effect source code is [`SEContext`](https://github.com/jbunke/stipple-effect/blob/master/src/com/jordanbunke/stipple_effect/project/SEContext.java).

---

## Functions

For an arbitrary `project` object named `P`, functions of the form `P.func_name(parameters) -> return_type` are __*value-returning functions*__, while functions of the form `P.func_name(parameters);` are __*void functions*__, which perform an action but return nothing.

### `get_frame_index`
```js
P.get_frame_index() -> int
```
Returns the current frame index of the project `P`.

### `set_frame_index`
```js
P.set_frame_index(int i);
```
Sets the active frame index of the project `P` to `i`.

**Fails:**

Any of the following will cause the function not to execute:
* `i < 0`
* `i >= P.get_frame_count()`

### `get_frame_durations`
```js
P.get_frame_durations() -> float[]
```
Returns the durations of the frames in the project `P` as an array of `float`. The value at each index in the array represents the relative duration of the frame with the equivalent frame index in `P`.

### `get_frame_duration`
```js
P.get_frame_duration(int i) -> float
```
Returns the duration of the frame at frame index `i` in the project `P` as a multiple of the duration of a standard frame (relative to the playback frame rate). For example, a frame that is to be displayed for twice as long as a standard frame will return `2.0`.

**Throws:**

Any of the following will result in a runtime error:
* `i < 0`
* `i >= P.get_frame_count()`

### `set_frame_duration`
```js
P.set_frame_duration(int i, float frame_duration);
```
Sets the frame duration of the frame at frame index `i` in the project `P` to `frame_duration`. This value represents how long a frame should be displayed relative to a standard frame, which has a frame duration of `1.0`.

**Fails:**

Any of the following will cause the function not to execute:
* `i < 0`
* `i >= P.get_frame_count()`
* `frame_duration < 0.1`
* `frame_duration > 20.0`

### `get_frame_count`
```js
P.get_frame_count() -> int
```
Returns the number of frames in the project `P`.

### `is_anim`
```js
P.is_anim() -> bool
```
Returns `true` if the project `P` has multiple frames, `false` otherwise (i.e. only has a single frame).

### ![](https://raw.githubusercontent.com/jbunke/stipple-effect/master/res/icons/new_frame.png) `add_frame`
```js
P.add_frame();
```
Adds a new frame to the project `P` directly after the current active frame. The new frame becomes the new active frame.

**Fails** if `P.get_frame_count() >= 300`

### ![](https://raw.githubusercontent.com/jbunke/stipple-effect/master/res/icons/duplicate_frame.png) `duplicate_frame`
```js
P.duplicate_frame();
```
Duplicates the current active frame of project `P` and places the duplicate directly after the initial frame. The duplicate frame becomes the new active frame.

**Fails** if `P.get_frame_count() >= 300`

### ![](https://raw.githubusercontent.com/jbunke/stipple-effect/master/res/icons/remove_frame.png) `remove_frame`
```js
P.remove_frame();
```
Removes the current active frame of the project `P`. If the frame to be removed is the first frame, the active frame becomes the new first frame after the removal. Otherwise, the new active frame becomes the frame before the frame that was removed.

**Fails** if `P.get_frame_count() == 1`

### ![](https://raw.githubusercontent.com/jbunke/stipple-effect/master/res/icons/move_frame_back.png) `move_frame_back`
```js
P.move_frame_back();
```
Swaps the current active frame of the project `P` with the preceding frame.

**Fails** if `P.get_frame_index() == 0`

### ![](https://raw.githubusercontent.com/jbunke/stipple-effect/master/res/icons/move_frame_forward.png) `move_frame_forward`
```js
P.move_frame_forward();
```
Swaps the current active frame of the project `P` with the following frame.

**Fails** if `P.get_frame_index() == P.get_frame_count() - 1`

### `get_layer`
1.  ```js
    P.get_layer() -> layer
    ```
    Returns the current editing layer of the project `P`.
2.  ```js
    P.get_layer(int i) -> layer
    ```
    Returns the layer at layer index `i` in project `P`.

    **Throws:**

    Any of the following will result in a runtime error:
    * `i < 0`
    * `i >= #|P.get_layers()`
3.  ```js
    P.get_layer(string name) -> layer
    ```
    Returns the lowest-indexed layer in `P` with a [name](layer.md/#get_name) matching `name`.

    No matching layer in `P` will result in a runtime error.

### `get_layers`
```js
P.get_layers() -> layer[]
```
Returns an array of all the layers in project `P`, with the lowest layer at index 0.

### `get_layer_index`
```js
P.get_layer_index() -> int
```
Returns the layer index of the current editing layer of project `P`.

### `set_layer_index`
```js
P.set_layer_index(int i);
```
Sets the editing layer index of project `P` to `i`. Layers are ordered from the bottom up, so an index of 0 will correspond to the lowest layer.

**Fails:**

Any of the following will cause the function not to execute:
* `i < 0`
* `i >= #|P.get_layers()`

### ![](https://raw.githubusercontent.com/jbunke/stipple-effect/master/res/icons/new_layer.png) `add_layer`
```js
P.add_layer();
```
Adds a new layer to the project `P` directly above the current editing layer. The new layer becomes the new editing layer.

**Fails** if `#|P.get_layers() >= 50`

### ![](https://raw.githubusercontent.com/jbunke/stipple-effect/master/res/icons/duplicate_layer.png) `duplicate_layer`
```js
P.duplicate_layer();
```
Duplicates the current editing layer of project `P` and places the duplicate directly on top of the initial layer. The duplicate layer becomes the new editing layer.

**Fails** if `#|P.get_layers() >= 50`

### ![](https://raw.githubusercontent.com/jbunke/stipple-effect/master/res/icons/remove_layer.png) `remove_layer`
```js
P.remove_layer();
```
Removes the current editing layer of the project `P`. If the layer to be removed is the bottommost layer, the editing layer becomes the new bottommost layer after the removal. Otherwise, the new editing layer becomes the layer below the layer that was removed.

**Fails** if `#|P.get_layers() == 1`

### ![](https://raw.githubusercontent.com/jbunke/stipple-effect/master/res/icons/move_layer_down.png) `move_layer_down`
```js
P.move_layer_down();
```
Swaps the current editing layer of the project `P` with the layer below.

**Fails** if `P.get_layer().index == 0`

### ![](https://raw.githubusercontent.com/jbunke/stipple-effect/master/res/icons/move_layer_up.png) `move_layer_up`
```js
P.move_layer_up();
```
Swaps the current editing layer of the project `P` with the layer above.

**Fails** if `P.get_layer().index == #|P.get_layers() - 1`

### ![](https://raw.githubusercontent.com/jbunke/stipple-effect/master/res/icons/merge_with_layer_below.png) `merge_with_below`
```js
P.merge_with_below();
```
Merges the current editing layer of the project `P` with the layer below it if the editing layer is not the lowest layer in `P`.

**Fails** if `P.get_layer().index == 0`

### ![](https://raw.githubusercontent.com/jbunke/stipple-effect/master/res/icons/flatten.png) `flatten`
```js
P.flatten();
```
Flattens project `P`, compressing all of its contents down to a single layer.

### `is_selected`
```js
P.is_selected(int x, int y) -> bool
```
Returns `true` if the pixel at `x`, `y` is part of the current selection in the project `P`, `false` otherwise.

**Note:**

`x` and `y` do not have to be within the bounds of the canvas of `P` to be included in its selection.

### `has_selection`
```js
P.has_selection() -> bool
```
Returns `true` if the project `P` currently has a selection, `false` otherwise.

### `get_selection`
```js
P.get_selection() -> int[]{}
```
Returns the current selection of the project `P` as a set of two-element integer arrays. For every `int[] coord` in the return set `int[]{}`, `coord[0]` is the pixel X coordinate and `coord[1]` is the pixel Y coordinate.

### `set_selection`
```js
P.set_selection(int[]{} selection);
```
Sets the current pixel selection of the project `P` to `selection`.

**Fails:**

Any of the following will cause the function not to execute:
* For any `int[] coord` in `selection`, `#|coord != 2`

### `select_all`
```js
P.select_all();
```
Sets the current pixel selection of the project `P` to be all the pixels of its canvas.

### `deselect`
```js
P.deselect();
```
Empties the current pixel selection of the project `P`.

### `invert_selection`
```js
P.invert_selection();
```
Inverts the current pixel selection of the project `P`. That is, for every pixel on the project canvas, it will be included in the updated selection if and only if it is not part of the current selection.

### ![](https://raw.githubusercontent.com/jbunke/stipple-effect/master/res/icons/save.png) `save`
```js
P.save();
```
Saves the project `P` if `P` has a valid save configuration (`save_config`). That is, `P` has been assigned a folder, a filename, a valid project type for its contents (whether STIP, single PNG, GIF, etc.) and any associated metadata.

### ![](https://raw.githubusercontent.com/jbunke/stipple-effect/master/res/icons/save_as.png) `save_as`
```js
P.save_as(save_config sc);
```
Attempts to set `sc` as the save configuration for `P` and save `P`.

If `sc` is an imcomplete configuration, `P` is neither saved nor has its existing save configuration overwritten by `sc`. `sc` can be incomplete due to:
* `sc` not having a folder
* `sc` having an empty filename

**Note:**

Invalid `save_config` objects cannot be successfully instantiated via script, but can be referenced by calling [`get_save_config()`](#get_save_config) on a project with an as-yet undefined save configuration.

### `get_save_config`
```js
P.get_save_config() -> save_config
```
Returns the `save_config` object associated with `P`.

### `get_width`
```js
P.get_width() -> int
```
Returns the pixel width of the canvas of `P`.

### `get_height`
```js
P.get_height() -> int
```
Returns the pixel height of the canvas of `P`.

### ![](https://raw.githubusercontent.com/jbunke/stipple-effect/master/res/icons/resize.png) `resize`
```js
P.resize(int w, int h);
```
Resizes the project `P` with a new canvas of dimensions `w` x `h` pixels.

**Fails:**

Any of the following will cause the function not to execute:
* `w <= 0`
* `w > 1920`
* `h <= 0`
* `h > 1080`

### ![](https://raw.githubusercontent.com/jbunke/stipple-effect/master/res/icons/pad.png) `pad`
```js
P.pad(int l, int r, int t, int b);
```
Pads the project `P` by `l` pixels to the left, `r` pixels to the right, `t` pixels upwards, and `b` pixels downwards. Arguments for `l`, `r`, `t` and `b` can be negative if one wants to trim the project rather than pad it in any direction.

**Fails:**

Any of the following will cause the function not to execute:
* `P.get_width() + l + r <= 0`
* `P.get_width() + l + r > 1920`
* `P.get_height() + t + b <= 0`
* `P.get_height() + t + b > 1080`

### ![](https://raw.githubusercontent.com/jbunke/stipple-effect/master/res/icons/stitch_split_frames.png) `stitch`
```js
P.stitch(int frames_per_dim, bool dim);
```
Stitches the frames of the project `P` together, allotting `frames_per_dim` frames to every row or column.

`dim` determines the sequencing order.
* If `dim` is `true`, the sequencing order is horizontal, and `frames_per_dim` frames are allotted to each __*row*__. Frames are sequenced left to right, top to bottom.
* If `dim` is `false`, the sequencing order is vertical, and `frames_per_dim` frames are allotted to each __*column*__. Frames are sequenced top to bottom, left to right.

**Fails:**

Any of the following will cause the function not to execute:
* `frames_per_dim > 300`
* `frames_per_dim <= 0`

**Reading material:**
* [Stitch operation in the documentation](../docs/sizing.md/#stitch-frames-into-sprite-sheet)
* [Dimension constants](global.md/#dimension-constants)

### ![](https://raw.githubusercontent.com/jbunke/stipple-effect/master/res/icons/stitch_split_frames.png) `split_px`
```js
P.split_px(int frm_w, int frm_h, bool dim, bool trunc_x, bool trunc_y);
```
Splits the project `P` into frames of `frm_w` x `frm_h` pixels each.

`dim` determines the sequencing order.
* If `dim` is `true`, the sequencing order is horizontal; frames are sequenced left to right, top to bottom.
* If `dim` is `false`, the sequencing order is vertical; frames are sequenced top to bottom, left to right.

If `trunc_x` is true, any remaining content on the X-axis will be truncated and discarded. If `trunc_x` is false and `P.get_width() % frm_w != 0`, an additional frame is allotted for every row that is partially populated by the remaining content. 

`trunc_y` follows from `trunc_x`.

**Fails:**

Any of the following will cause the function not to execute:
* `frm_w <= 0`
* `frm_w > P.get_width()`
* `frm_h <= 0`
* `frm_h > P.get_height()`

**Reading material:**
* [Split operation in the documentation](../docs/sizing.md/#split-sprite-sheet-into-frames)
* [Dimension constants](global.md/#dimension-constants)

### ![](https://raw.githubusercontent.com/jbunke/stipple-effect/master/res/icons/stitch_split_frames.png) `split`
```js
P.split(int cols, int rows, bool dim, bool trunc_x, bool trunc_y);
```
Splits the project `P` into `cols` x `rows` frames where `cols` is the number of columns and `rows` is the number of rows into which `P` is partitioned.

`dim` determines the sequencing order.
* If `dim` is `true`, the sequencing order is horizontal; frames are sequenced left to right, top to bottom.
* If `dim` is `false`, the sequencing order is vertical; frames are sequenced top to bottom, left to right.

If `trunc_x` is true, any remaining content on the X-axis will be truncated and discarded. If `trunc_x` is false and `P.get_width() % cols != 0`, an additional frame is allotted for every row that is partially populated by the remaining content. In this case, the project would end up being divided into `cols + 1` columns rather than `cols` columns.

`trunc_y` follows from `trunc_x`.

**Fails:**

Any of the following will cause the function not to execute:
* `cols <= 0`
* `rows <= 0`
* `cols * row > 300`

**Reading material:**
* [Split operation in the documentation](../docs/sizing.md/#split-sprite-sheet-into-frames)
* [Dimension constants](global.md/#dimension-constants)

---

## Color actions

**Note on color action functions:**

The following functions are perform an action over a given __*scope*__ of the project. All of them include these three parameters: `int scope, bool include_disabled, bool ignore_selection`.

An invalid `scope` value will result in a runtime error.

The flag `include_disabled` will include disabled/invisible layers in the operation if `scope` contains multiple layers (`$SE.PROJECT`, `$SE.FRAME`).

The flag `ignore_selection` will apply the operation to the entire canvas if it is `true` or if the project has no selection. If `ignore_selection` is false and the project has a selection, the operation will only be applied to the pixels in the selection.

Reading material:
* [Scope in the documentation](../docs/scope.md)
* [Scope constants](global.md/#scope-constants)

### ![](https://raw.githubusercontent.com/jbunke/stipple-effect/master/res/icons/palettize.png) `palettize`
```js
P.palettize(palette pal, int scope, bool include_disabled, bool ignore_selection);
```
Maps the colors of the pixels in the scope `scope` in the project `P` to their nearest color in the palette `pal`.

See [above](#color-actions) for details about `scope` and the flags `include_disabled` and `ignore_selection`.

### ![](https://raw.githubusercontent.com/jbunke/stipple-effect/master/res/icons/contents_to_palette.png) `extract_to_pal`
```js
P.extract_to_pal(palette pal, int scope, bool include_disabled, bool ignore_selection);
```
Extracts the colors of the pixels in the scope `scope` in the project `P` to the palette `pal`.

See [above](#color-actions) for details about `scope` and the flags `include_disabled` and `ignore_selection`.

### ![](https://raw.githubusercontent.com/jbunke/stipple-effect/master/res/icons/hsv_shift.png) `hsv_shift`
```js
P.hsv_shift(int scope, bool include_disabled, bool ignore_selection, int h_shift, N s_shift, N v_shift);
```
Shifts the HSV levels of the pixels in the scope `scope` in the project `P` by the shift values `h_shift`, `s_shift` and `v_shift`. The type `N` represents a numeric type: either an `int` or a `float`.

`h_shift` ranges from `-180` to `180`, where `0` is no change.

`s_shift` can be either an `int` or a `float`:
* As an `int`, it represents a shift that ranges from `-255` to `255`, where `0` is no change. The resulting value (`s + s_shift`) will be clamped between `0` and `255`.
* As a `float`, it represents a scale factor that ranges from `0.0` to `50.0`, where `1.0` is no change.

`v_shift` can be either an `int` or a `float`:
* As an `int`, it represents a shift that ranges from `-255` to `255`, where `0` is no change. The resulting value (`v + v_shift`) will be clamped between `0` and `255`.
* As a `float`, it represents a scale factor that ranges from `0.0` to `50.0`, where `1.0` is no change.

See [above](#color-actions) for details about `scope` and the flags `include_disabled` and `ignore_selection`.

### ![](https://raw.githubusercontent.com/jbunke/stipple-effect/master/res/icons/color_script.png) `color_script`
```js
P.color_script(int scope, bool include_disabled, bool ignore_selection, script cs);
```
Modifies the colors of the pixels in the scope `scope` in the project `P` according to the transformation defined by the color script `cs`.

See [above](#color-actions) for details about `scope` and the flags `include_disabled` and `ignore_selection`.

**Note:**
`cs` must have a valid color script type signature: `(color -> color)`. Attempting to pass an invalid script will result in a runtime error.

Reading material:
* [Color scripts in the documentation](../docs/color-scripts.md)
