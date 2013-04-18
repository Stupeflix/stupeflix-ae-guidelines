
Expressions and Bézier Curves
=============================

Cloud Renderer
--------------

Expressions, Bezier curves and Hold keyframes are not natively supported by our engine, but they can easily be turned into linear keyframes while preserving ease.

For layers with Bezier Curves, just Alt-Clic on the property stopwatch to create an expression and press the numeric keypad Enter key. Now select the property and go to:

- **Animation > Keyframe Assistant > Convert Expression to Keyframes**

For properties with expressions, select them and go to:

- **Animation > Keyframe Assistant > Convert Expression to Keyframes**

For both operations, you can select multiple properties.

Then, with all the newly created keyframes selected, crtl (or cmd) click on any of them to turn them into diamond shaped keyframes (standard keyframe) instead of roaving keyframes (round shaped keyframes).

iOS Renderer
------------

On our iOS Renderer, Bézier curves are natively supported by our engine, so no need to rasterize (bake) them using the above methodology. You'll still need to bake the expressions.