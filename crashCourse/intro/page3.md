
# Enter and Append
This is the most common way to add data to the chart.

```
function addItems(){
 	 
    var svg = d3.select('#content').append('svg')
      .attr('width', 730)
      .attr('height', 120)
     
 
    svg.selectAll("circle")
      .data(data1)
      .enter()
      .append("circle")
      .attr("cx", function(d, i){return 50+i*70;})
      .attr("cy", 50)
      .attr("r", function(d){return d.value;})
      .style("fill", function(d){return d.color;});
} 
```
So in this case, we grab the dom element #content and add an SVG element to it.
Then we take the data and enter the parent node each time to append a circle element.

We can decorate each element as well.


https://jsbin.com/ritihaw/edit?html,js,console,output

There is one problem.  If you click on the join twice, you get a second chart.
Opps.


Lets fix it

https://jsbin.com/jekelij/edit?html,js,console,output

Ok...so now we can click add, and it really does not do a whole lot.

If we click modify, we can modify the data, however, since there are only 3 
items,  we will modify the three items and the old fourth one remains.




## General Update Pattern

I would suggest at this point looking at
https://www.d3indepth.com/enterexit/
for more examples.  

But we ultimate end up with the *general update pattern.*

https://bl.ocks.org/mbostock/3808234

see also join
https://www.freecodecamp.org/news/how-to-work-with-d3-jss-general-update-pattern-8adce8d55418/


https://jsbin.com/qixejuy/edit?html,js,console,output