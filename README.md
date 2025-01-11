# Stipple Effect API specification

This is the API (application programming interface) specification for scripting in *Stipple Effect*. It covers all the extensions made to the [*DeltaScript* base language![](./assets/external.png)](https://github.com/jbunke/deltascript) for scripting in *Stipple Effect*.

For a general overview of scripting, please visit [the documentation](../docs/scripting.md).

### Content

* Namespaces
  * [Global namespace (`$SE`)](global.md)
  * [`$Graphics`](graphics.md)
  * [`$Math`](math.md)
* Types
  * [`layer`](layer.md)
  * [`light`](light.md)
  * [`palette`](palette.md)
  * [`project`](project.md)
  * [`save_config`](save_config.md)
  * [`script`](script.md)
* *DeltaScript* built-in types extended for *Stipple Effect*
  * [`color`](color.md)

### Changelog

See changes made to the API across *Stipple Effect* releases [here](changelog.md).

---

**SEE ALSO**

* [Script examples![](./assets/external.png)](https://github.com/stipple-effect/script-examples)
* [*DeltaScript for Stipple Effect* - VS Code syntax highlighting extension![](./assets/external.png)](https://marketplace.visualstudio.com/items?itemName=jordanbunke.deltascript-for-stipple-effect)
* [*Stipple Effect* video playlist (w/ tutorials)![](./assets/external.png)](https://www.youtube.com/playlist?list=PLy71S74rTLnPEwYYtAXvh2er8QBvWIwRL)
* [*Stipple Effect* source code![](./assets/external.png)](https://github.com/stipple-effect/stipple-effect)
