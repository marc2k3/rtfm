# Gradients

!!! note
	`gr` on this page refers to [IJSGraphics](../api/interfaces/IJSGraphics.md)

Using `gr.FillRectangle` as an example, most will know the last argument is a
`number` to represent a colour.

```js
gr.FillRectangle(x, y, w, h, colour);
```

The colour argument can also be `string`. This represents a `brush` which is described below.

## Stops
Before creating a `brush`, we need to define the colours we want to use. So the first
thing to do is create an array of [stops](https://learn.microsoft.com/en-us/windows/win32/api/d2d1/nn-d2d1-id2d1gradientstopcollection#remarks).
In this component, an array of `stops` must be at least `2` in length.

A `stop` is a `position` and a `colour`. The min/max values for a `position` is `0` and `1`.
Anyone reading this should be familiar with valid `colour` values!

So the simplest example can be:

```js
var stops = [
	[0, RGB(255, 0, 0)],
	[1, RGB(0, 0, 255)],
];
```

If you want to insert more colours:

```js
var stops = [
	[0, RGB(255, 0, 0)],
	[0.5, RGB(0, 255, 0)],
	[1, RGB(0, 0, 255)],
];
```

## Linear brush
Now we know what `stops` are, we can create a [linear brush](https://learn.microsoft.com/en-us/windows/win32/direct2d/direct2d-brushes-overview#using-linear-gradient-brushes).

A linear brush must have 3 properties: `Start`, `End` and `Stops`.

```js
var linear_brush = {
	Start : [0, 0], // x and y values
	End : [0, 0], // x and y values
	Stops: stops
};
```

The `Start` and `End` values are relative to the `x` and `y` positions of the rectangle.

If we lift `FillGradientRectangle` from `helpers.txt`, we can inspect a working example.

```js
function FillGradientRectangle(gr, x, y, w, h, direction, colour1, colour2) {
	var stops = [
		[0, colour1],
		[1, colour2]
	];

	var brush = {Start : [0, 0], Stops: stops};

	if (direction == 0) // vertical
		brush.End = [0, h];
	else // horizontal
		brush.End = [w, 0];

	gr.FillRectangle(x, y, w, h, JSON.stringify(brush));
}
```

!!! note
	See the final step there is to use `JSON.stringify` on the `brush` object. `JavaScript` objects
	can not be passed directly to the component so it must be a `string`.

The `Start` `x` and `y` values never change. The `End` positions change depending on the effect you want.

While that example is fixed to vertical or horizontal, there are no limitations when creating your
own.

For a diagonal effect, you can do something like this:

!!! example
	```js
	// ==PREPROCESSOR==
	// @import "%fb2k_component_path%helpers.txt"
	// ==/PREPROCESSOR==

	var stops = [
		[0, RGB(255, 0, 0)],
		[1, RGB(0, 0, 255)],
	];

	var linear_brush = {
		Stops: stops,
		Start: [0, 0]
	};

	function on_paint(gr) {
		linear_brush.End = [window.Width, window.Height];
		gr.FillRectangle(0, 0, window.Width, window.Height, JSON.stringify(linear_brush));
	}
	```
