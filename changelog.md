# API Changelog

[`< Home`](README.md)

## 1.2.2

### Added:
* `light` type
* New namespaces and associated functions and constants
  * `$Graphics`
  * `$Math`

## 1.2.0

### Added:
* New types
  * `script`
  * `save_config`
* Constants 
  * Scope constants that evaluate to `int`
    * `$SE.PROJECT` = `0`
    * `$SE.LAYER` = `1`
    * `$SE.FRAME` = `2`
    * `$SE.CEL` = `3`
  * Save type constants that evaluate to `int`
    * `$SE.NATIVE` = `0`
    * `$SE.PNG_SHEET` = `1`
    * `$SE.PNG_SEPARATE` = `2`
    * `$SE.GIF` = `3`
    * `$SE.MP4` = `4`
  * Dimension constants that evaluate to `bool`
    * `$SE.HORZ` = `true`
    * `$SE.VERT` = `false`
  * Added `layer` functions; for some `layer L`...
    * ```js
      L.get_name() -> string
      ```
    * ```js
      L.set_name(string);
      ```
  * Added `project` functions; for some `project P`...
    * ```js
      P.get_width() -> int
      ```
    * ```js
      P.get_height() -> int
      ```
    * ```js
      P.get_layer(string) -> layer
      ```
    * ```js
      P.get_save_config() -> save_config
      ```
    * ```js
      P.save_as(save_config);
      ```
  * Added global functions
    * ```js
      $SE.read_script(string) -> script
      ```
    * ```js
      $SE.new_save_config(string[], string, int) -> save_config
      ```
    * ```js
      $SE.transform(project, script, bool, bool) -> project
      ```
    * ```js
      $SE.transform(project, script) -> project
      ```
    * ```js
      $SE.new_project(int, int, bool) -> project
      ```

### Changed:
* Renamed `layer` functions; for some `layer L`... 
  * Renamed `L.get_frame(int)` to `L.get_cel(int)`
  * Renamed `L.set_frame(int, image)` to `L.set_cel(int, image)`
  * Renamed `L.wipe_frame(int, image)` to `L.wipe_cel(int, image)`
  * Renamed `L.edit_frame(int, image)` to `L.edit_cel(int, image)`
  * Renamed `L.link_frames()` to `L.link_cels()`
  * Renamed `L.unlink_frames()` to `L.unlink_cels()`
  * Renamed `L.disable_layer()` to `L.disable()`
  * Renamed `L.enable_layer()` to `L.enable()`

## 1.1.0

### Removed:

* Removed the property `mutable` of the type `palette`

### Changed:

* API references to `LAYER-FRAME` have been renamed to `CEL`; no changed behaviour

## 0.5.0

### Added:

* `project` frame duration functions:
  * ```js
    P.get_frame_duration(int i) -> float
    ```
  * ```js
    P.get_frame_durations() -> float[]
    ```
  * ```js
    P.set_frame_duration(int i, float frame_duration);
    ```

### Changed:

* Separated selection from scope in color actions
  * Modified `scope` enumeration:
    ```js
    0: PROJECT
    1: LAYER
    2: FRAME
    3: LAYER_FRAME
    ```
  * Changed `project` color action function signatures:
    * ```js
      P.palettize(palette pal, int scope, bool include_disabled, bool ignore_selection);
      ```
    * ```js
      P.extract_to_pal(palette pal, int scope, bool include_disabled, bool ignore_selection);
      ```
    * ```js
      P.hsv_shift(int scope, bool include_disabled, bool ignore_selection, int h_shift, N s_shift, N v_shift);
      ```
    * ```js
      P.color_script(int scope, bool include_disabled, bool ignore_selection, string script_path);
      ```

## 0.4.2

**Note: This update completely redesigned the API and altered the syntax of every API function. Scripts that utilize API functions that were written for versions 0.4.0 or 0.4.1 will need to be rewritten in order to execute on subsequent versions of Stipple Effect.**

### Added:

* `palette` type
* Global namespace `$SE`
* `project` color action functions:
  * ```js
    P.palettize(palette pal, int scope, bool include_disabled);
    ```
  * ```js
    P.extract_to_pal(palette pal, int scope, bool include_disabled);
    ```
  * ```js
    P.hsv_shift(int scope, bool include_disabled, int h_shift, float s_shift, float v_shift);
    ```
  * ```js
    P.color_script(int scope, bool include_disabled, string script_path);
    ```

### Changed:

* Renamed `set_frame_content` to `set_frame`
* Renamed `get_frame_content` to `get_frame`

## 0.4.0 - The Scripting Update

* Initial release of the scripting API