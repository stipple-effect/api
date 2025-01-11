[`< API`](README.md)

# `layer`

`layer` objects created in scripts are internally represented by the [`LayerRep`![](./assets/external.png)](https://github.com/stipple-effect/stipple-effect/blob/master/src/com/jordanbunke/stipple_effect/scripting/util/LayerRep.java) class from the *Stipple Effect* source code.

**Note:**

`LayerRep` stores an immutable reference to the project that contains the layer, and to its layer index. This means that a `layer` reference in script can be "spoiled" - i.e. cease to refer to the same layer or no longer refer to a valid layer at all - if the number of layers in the project are changed, or if the order of the layers in the project is changed.

---

## Properties

These definitions use the arbitrary `layer` object `L` as the caller.

### `index`
```js
L.index -> int
```
Returns the layer index of `L`. The lowest layer in a project has an index of `0`.

### `project`
```js
L.project -> project
```
Returns the `project` to which `L` belongs.

---

## Functions

For an arbitrary `layer` object named `L`, functions of the form `L.func_name(parameters) -> return_type` are __*value-returning functions*__, while functions of the form `L.func_name(parameters);` are __*void functions*__, which perform an action but return nothing.

### `is_linked`
```js
L.is_linked() -> bool
```
Returns `true` if the cels in layer `L` are linked, `false` otherwise.

### ![](https://raw.githubusercontent.com/stipple-effect/stipple-effect/master/res/icons/frames_linked.png) `link_cels`
```js
L.link_cels();
```
Links the cels of the layer `L` together. This means that all of the cels in `L` will display the same image, and that changes made on any cel of layer `L` will be propagated to all of the cels of `L`. The linked content will be set from the cel at the current frame index.

### ![](https://raw.githubusercontent.com/stipple-effect/stipple-effect/master/res/icons/frames_unlinked.png) `unlink_cels`
```js
L.unlink_cels();
```
Unlinks the cels of the layer `L`. If `L` was previously linked, all its cel will still initially appear to be the same, but can now be modified independently.

### `is_enabled`
```js
L.is_enabled() -> bool
```
Returns `true` if the layer `L` is enabled i.e. visible, `false` otherwise.

### ![](https://raw.githubusercontent.com/stipple-effect/stipple-effect/master/res/icons/layer_disabled.png) `disable`
```js
L.disable();
```
Disables the layer `L`, i.e. makes it invisible.

### ![](https://raw.githubusercontent.com/stipple-effect/stipple-effect/master/res/icons/layer_enabled.png) `enable`
```js
L.enable();
```
Enables the layer `L`, i.e. makes it visible.

### `is_opaque`
```js
L.is_opaque() -> bool
```
Returns `true` if the layer `L` has an opacity of `1.0` (represented as 255 in Stipple Effect), `false` otherwise.

### `get_opacity`
```js
L.get_opacity() -> float
```
Returns the opacity of layer `L` as a float ranging from `0.0` (transparent) to `1.0` (opaque).

### `set_opacity`
```js
L.set_opacity(float opacity);
```
Sets the opacity of the layer `L` to `opacity`.

**Fails:**

Any of the following will cause the function not to execute:

* `opacity < 0.0`
* `opacity > 1.0`

### `get_name`
```js
L.get_name() -> string
```
Returns the name of the layer `L`.

### `set_name`
```js
L.set_name(string name);
```
Sets the name of the layer `L` to `name`.

**Fails:**

Any of the following will cause the function not to execute:

* If `name` is `""`
* If `name` contains any of the following characters:
    ```js
    { '/', '\\', ':', '*', '?', '"', '<', '>', '|', '{', '}' }
    ```

### `get_cel`
```js
L.get_cel(int i) -> image
```
Returns the cel contents of layer `L` at frame index `i`. If the cels of layer `L` are linked, the function will return the linked content.

**Throws:**

Any of the following will result in a runtime error:

* `i < 0`
* `i >= L.project.get_frame_count()`

### `set_cel`
```js
L.set_cel(int i, image content);
```
Sets the content to the cel at index `i` of the layer `L` to the image `content`.

**Fails:**

Any of the following will cause the function not to execute:

* `content.w != L.project.get_width()`
* `content.h != L.project.get_height()`
* `i < 0`
* `i >= L.project.get_frame_count()`

### `edit_cel`
```js
L.edit_cel(int i, image drawn);
```
Draws the image `drawn` on top of the cel's existing contents at position (0, 0).

**Fails:**

Any of the following will cause the function not to execute:

* `i < 0`
* `i >= L.project.get_frame_count()`

### `wipe_cel`
```js
L.wipe_cel(int i);
```
Erases the contents of the cel at index `i` of the layer `L`. Resultingly, cel `i` of `L` will consist of a fully transparent image.

**Fails:**

Any of the following will cause the function not to execute:

* `i < 0`
* `i >= L.project.get_frame_count()`
