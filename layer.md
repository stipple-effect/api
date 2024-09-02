<!-- Proofread and update for 1.2.0 -->
<!-- TODO
    * L.get_name() -> string
    * L.set_name(string);
    * Renames
      * Renamed `L.get_frame(int)` to `L.get_cel(int)`
      * Renamed `L.set_frame(int, image)` to `L.set_cel(int, image)`
      * Renamed `L.edit_frame(int, image)` to `L.edit_cel(int, image)`
      * Renamed `L.link_frames()` to `L.link_cels()`
      * Renamed `L.unlink_frames()` to `L.unlink_cels()`
      * Renamed `L.disable_layer()` to `L.disable()`
      * Renamed `L.enable_layer()` to `L.enable()`
-->

# `layer`

[`< API`](README.md)

`layer`'s correspondent type in the Stippe Effect source code is [`LayerRep`](https://github.com/jbunke/stipple-effect/blob/master/src/com/jordanbunke/stipple_effect/scripting/util/LayerRep.java).

**Note:** `LayerRep` stores an immutable reference to the project that contains the layer, and to its layer index. This means that a `layer` reference in script can be "spoiled" - i.e. cease to refer to the same layer or no longer refer to a valid layer at all - if the number of layers in the project are changed, or if the order of the layers in the project is changed.

---

## Properties

<!-- TODO -->

---

For an arbitrary `layer` object named `L`, functions of the form `L.func_name(parameters) -> return_type` are __*value-returning functions*__, while functions of the form `L.func_name(parameters);` are __*void functions*__, which perform an action but return nothing.

<!-- TODO -->