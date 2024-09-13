# `script`

[`< API`](README.md)

`script`'s correspondent type in the Stippe Effect source code is the [*Delta Time*](https://github.com/jbunke/delta-time) class [`HeadFuncNode`](https://github.com/jbunke/delta-time/blob/master/script/src/com/jordanbunke/delta_time/scripting/ast/nodes/function/HeadFuncNode.java).

---

## Functions

For an arbitrary `script` object named `S`, functions of the form `S.func_name(parameters) -> return_type` are __*value-returning functions*__, while functions of the form `S.func_name(parameters);` are __*void functions*__, which perform an action but return nothing.

### `run`
1. ```js
   S.run(A) -> R
   ```
   Runs the child script `S` from a parent script and returns the result of the child script execution as some value `R`. `A` is a placeholder for zero or more comma-separated arguments passed into the script.
   
   It is assumed that the writer of the parent script knows the type signature of `S`, and that:
   
   * any arguments `A` match the parameters of `S`'s header function
   * `S` returns a value
   * `R` is treated as an instance of `S`'s return type in the parent script

   Failure to comply with any of these assertions will result in a runtime error.

2. ```js
   S.run(A);
   ```
   Runs the child script `S` from a parent script. `A` is a placeholder for zero or more comma-separated arguments passed into the script.

   It is assumed that the writer of the parent script knows the type signature of `S`. Passing a series of arguments `A` into `S` that does not match the parameters of `S`'s header function will result in a runtime error.

   **Note:**
   
   Void `run()` can be called on a child script `S` that has a return type; the value returned by `S` will simply be ignored.

Reading material:

* [Script structure in the documentation](../docs/scripting.md#syntax)
