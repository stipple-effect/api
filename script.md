<!-- Proofread and update for 1.2.0 -->
<!-- TODO
    * S.run(?) -> ?
    * S.run(?);
-->

# `script`

[`< API`](README.md)

`script`'s correspondent type in the Stippe Effect source code is the [*Delta Time*](https://github.com/jbunke/delta-time) class [`HeadFuncNode`](https://github.com/jbunke/delta-time/blob/master/script/src/com/jordanbunke/delta_time/scripting/ast/nodes/function/HeadFuncNode.java).

---

## Functions

For an arbitrary `script` object named `S`, functions of the form `S.func_name(parameters) -> return_type` are __*value-returning functions*__, while functions of the form `S.func_name(parameters);` are __*void functions*__, which perform an action but return nothing.

<!-- TODO -->