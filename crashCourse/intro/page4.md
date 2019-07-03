
# Scale functions and Axis

## Scale Functions
Scalars are very important with D3 because you pretty much always want to scale your image into a box.  These are functions that take an input and map it to an output.

Inputs can be values, time, ordinals. Outputs could be things like a coordinate, length, radius, color or even another ordinal.

Examples:
 - Translate a value to a radius
 - Translate a score to a number of stars
 - Translate the number of errors to a color.

 An example would be

 ```
  var xScale = d3.scaleLinear()
                .domain(0,100)
                .range([0, 1000])
 ```
 In this case a call to `xScale(40)` should return 400.

It can even interpolate between colors.

```
var color = d3.scaleLinear([10, 100], ["brown", "steelblue"]);
```

For a small sample of using scale functions, 
see here: https://jsbin.com/jezebal/edit?html,js,output


Other features include
 - Log and Power Scaling
 - Interpolations
 - Clamping
 - Time Scales

Even Piecewise scaling is allowed

```
var color = d3.scaleLinear()
    .domain([-1, 0, 1])
    .range(["red", "white", "green"]);
```


See [https://github.com/d3/d3-scale](https://github.com/d3/d3-scale) for a comprehensive list.

## Axes

So now that we can scale things, we can put up things like reference axes.

These are built in functions.

Lets look at a small example

https://jsbin.com/jenures/edit?html,js,output

In this case, we have done a standard bubble chart.
Note that the scale functions are deeply tied to the margins.

you will see code like this all the time

```
var margin = {top: 20, right: 20, bottom: 30, left: 50},
    width = 500 - margin.left - margin.right,
    height = 100 - margin.top - margin.bottom;
```
To make it responsive, you usually locate the bounding box and then work from there.
If the size of the view changes, you can event off of it and resize accordingly.
 
## Resizing Axes
If things like your max value change, you need to resize your axes as well as your 
data.  Here is an example the demonstrates this.


https://jsbin.com/zurogab/edit?html,js,console,output

In this case, we have combined a few things.
The XAxis call and scale are variables.

An initial value is set, but as the data changes, so do the scales.

