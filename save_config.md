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
Sets the file path of the parent folder for `SC` to `folder`. Each directory must be included as a unique `string` element in `folder`.

For example, an intended save destination of `C:\Desktop\game\assets` should be expressed as an argument for `folder` as `["C:", "Desktop", "game", "assets"]`.

**Constraints:**
* `#|folder > 0`
* `folder` must be a valid directory in the file system

### `set_filename`
```js
SC.set_filename(string filename);
```

Sets the filename of `SC` to `filename`. Note that `filename` refers only to the base name of the file. For a file saved to `C:\Desktop\example.png`, `filename` would be `"example"`, omitting the file type extension and the folder path.

**Constraints:**
* `#|filename > 0`
* ```js
  for (char disallowed in ['/', '\\', ':', '*', '?', '"', '<', '>', '|', '{', '}'])
      !filename.has(disallowed)
  ```

### `set_save_type`
```js
SC.set_save_type(int save_type);
```
Sets the save type of `SC` to `save_type`.

An invalid `save_type` will result in a runtime error.

Reading material:
* [Save type constants](global.md/#save-type-constants)

### `set_scale_up`
```js
SC.set_scale_up(int scale_up);
```
Sets the scale factor of `SC` to `scale_up`.

**Constraints:**
* `scale_up > 0`
* `scale_up <= 20`

**Note:** This is an export option. It is irrelevant when the save type is `$SE.NATIVE`.

### `set_fps`
```js
SC.set_fps(int fps);
```

Sets the playback speed for `SC` to `fps` frames per second. 

A project's frame's duration property will be divided by `fps` to determine how long each frame should be displayed for. For example, a frame with a duration factor of `1.5` will be displayed for 0.15 seconds when exported with an `fps` of `10`, as 1.5x / 10 [Hz](https://en.wikipedia.org/wiki/Hertz) = 0.15 s.

**Note:** This is an export option for animated media that is only relevant if the save type is `$SE.GIF` or `$SE.MP4`.

Reading material:

* [Frame duration in the documentation](https://github.com/jbunke/se-docs/blob/master/frame-duration.md)

### `set_dim`
```js
SC.set_dim(bool dim);
```
Sets the sequencing order of `SC` to `dim`:

* If `dim` is `true`, the sequencing order is horizontal; frames are sequenced per row - left to right, top to bottom.
* If `dim` is `false`, the sequencing order is vertical; frames are sequenced per column - top to bottom, left to right.

**Note:** This is an export option that is only relevant when the save type is `$SE.PNG_SHEET`.

Reading material:

* [Dimension constants](global.md/#dimension-constants)

### `set_frames_per_dim`
```js
SC.set_frames_per_dim(int frames_per_dim);
```
Sets the number of frames to be sequenced on each row or column of an exported sprite sheet by `SC` to `frames_per_dim`.

**Constraints:**
* `frames_per_dim > 0`

**Note:** This is an export option that is only relevant when the save type is `$SE.PNG_SHEET`.

### `unbounded`
```js
SC.unbounded();
```
If `SC` is configured to only export a subset of a project's frames, calling `unbounded()` will disable that configuration and set `SC` to export all project frames.

**Note:** This is an export option. It is irrelevant when the save type is `$SE.NATIVE`.

### `set_lower`
```js
SC.set_lower(int lower_bound);
```
Sets `SC` to only export a subset of a project's frames, with the lower bound frame index (inclusive) marked by `lower_bound`.

**Constraints:**
* `lower_bound >= 0`

**Note:** This is an export option. It is irrelevant when the save type is `$SE.NATIVE`.

### `set_upper`
```js
SC.set_upper(int upper_bound);
```
Sets `SC` to only export a subset of a project's frames, with the upper bound frame index (**inclusive**) marked by `upper_bound`.

**Constraints:**
* `upper_bound >= 0`

**Note:** This is an export option. It is irrelevant when the save type is `$SE.NATIVE`.

### `set_prefix`
```js
SC.set_prefix(string prefix);
```
If `SC` is configured to export frames separately, each frame file that is exported will carry a prefix (infix) of `prefix` before the frame number.

File name format: `folder + filename + prefix + frame_number + suffix + type_extension`

**Constraints:**
* `#|prefix <= 5`
* ```js
  for (char disallowed in ['/', '\\', ':', '*', '?', '"', '<', '>', '|', '{', '}'])
      !prefix.has(disallowed)
  ```

**Note:** This is an export option that is only relevant when the save type is `$SE.PNG_SEPARATE`.

### `set_suffix`
```js
SC.set_suffix(string suffix);
```
If `SC` is configured to export frames separately, each frame file that is exported will be appended with a suffix of `suffix` after the frame number.

File name format: `folder + filename + prefix + frame_number + suffix + type_extension`

**Constraints:**
* `#|suffix <= 5`
* ```js
  for (char disallowed in ['/', '\\', ':', '*', '?', '"', '<', '>', '|', '{', '}'])
      !suffix.has(disallowed)
  ```

**Note:** This is an export option that is only relevant when the save type is `$SE.PNG_SEPARATE`.

### `set_count_from`
```js
SC.set_count_from(int count_from);
```
If `SC` is configured to export frames separately, each frame file that is exported will be numbered incrementally starting from `count_from`.

**Note:** This is an export option that is only relevant when the save type is `$SE.PNG_SEPARATE`.
