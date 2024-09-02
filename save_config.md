# `save_config`

[`< API`](README.md)

`save_config`'s correspondent type in the Stippe Effect source code is [`SaveConfig`](https://github.com/jbunke/stipple-effect/blob/master/src/com/jordanbunke/stipple_effect/project/SaveConfig.java).

---

## Functions

For an arbitrary `save_config` object named `SC`, functions of the form `SC.func_name(parameters) -> return_type` are __*value-returning functions*__, while functions of the form `SC.func_name(parameters);` are __*void functions*__, which perform an action but return nothing.

### `set_folder`
```js
SC.set_folder(string[] folder);
```
<!-- TODO -->

### `set_filename`
```js
SC.set_filename(string filename);
```
<!-- TODO -->

### `set_save_type`
```js
SC.set_save_type(int save_type);
```
<!-- TODO -->

Reading material:
* [Save types in the documentation](TODO)
* [Save type constants](global.md/#save-type-constants)

### `set_scale_up`
```js
SC.set_scale_up(int scale_up);
```
<!-- TODO -->

**Note:** This is an export option. It is irrelevant when the save type is `$SE.NATIVE`.

### `set_fps`
```js
SC.set_fps(int fps);
```
<!-- TODO -->

**Note:** This is an export option for animated media that is only relevant if the save type is `$SE.GIF` or `$SE.MP4`.

### `set_dim`
```js
SC.set_dim(bool dim);
```
<!-- TODO -->

**Note:** This is an export option that is only relevant when the save type is `$SE.PNG_SHEET`.

### `set_frames_per_dim`
```js
SC.set_frames_per_dim(int frames_per_dim);
```
<!-- TODO -->

**Note:** This is an export option that is only relevant when the save type is `$SE.PNG_SHEET`.

### `unbounded`
```js
SC.unbounded();
```
<!-- TODO -->

**Note:** This is an export option. It is irrelevant when the save type is `$SE.NATIVE`.

### `set_lower`
```js
SC.set_lower(int lower_bound);
```
<!-- TODO -->

**Note:** This is an export option. It is irrelevant when the save type is `$SE.NATIVE`.

### `set_upper`
```js
SC.set_upper(int upper_bound);
```
<!-- TODO -->

**Note:** This is an export option. It is irrelevant when the save type is `$SE.NATIVE`.

### `set_prefix`
```js
SC.set_prefix(string prefix);
```
<!-- TODO -->

**Note:** This is an export option that is only relevant when the save type is `$SE.PNG_SEPARATE`.

### `set_suffix`
```js
SC.set_suffix(string suffix);
```
<!-- TODO -->

**Note:** This is an export option that is only relevant when the save type is `$SE.PNG_SEPARATE`.

### `set_count_from`
```js
SC.set_count_from(int count_from);
```
<!-- TODO -->

**Note:** This is an export option that is only relevant when the save type is `$SE.PNG_SEPARATE`.
