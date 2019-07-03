
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
You will note, that in this case, there are no circles in the html to start with.
This is normal and the regular way to do this. (Will make sense in a bit).

Once in the SVG element, we use the append function to add as many elements as there are in the data.


https://jsbin.com/ritihaw/edit?html,js,console,output

There is one problem.  If you click on the join twice, you get a second chart.
Opps.


Lets fix it

https://jsbin.com/jekelij/edit?html,js,console,output

Ok, so in this case, we add the SVG element as part of the setup.  No need to do that twice.  Then we add the 4 elements from the data.

If we click add again, not much new happens.

If we click modify, we can modify the data, however, since there are only 3 
items in the new set,  we will modify the three items and the old fourth one remains.

Note there is not an `append()` for the modify case.


## General Update Pattern

So the size of our data will change.  We do want to add new items, if they are new, modify things that are already there and delete items that no longer exist.

Luckily there is a a pattern to this called the *general update pattern.*

### Links you should follow up on 
I would suggest at this point looking at
https://www.d3indepth.com/enterexit/
for more examples.  

https://bl.ocks.org/mbostock/3808234

see also join
https://www.freecodecamp.org/news/how-to-work-with-d3-jss-general-update-pattern-8adce8d55418/


In this pattern, we take the selection and associate the data to the collecion and then call `enter()`.
At this point, the chaining will either add items if they are new, or modify items that are already exist.  Its pretty magical.

Finally, the `exit().remove()` will trim items that are not associated with data.

```
function update(data) {
  
  var u = d3.select('#content svg')
    .selectAll('circle')
    .data(data);

  u.enter()
    .append('circle')
    .merge(u)
    .attr("cx", function(d, i){return 50+i*70;})
    .attr("cy", 50)
    .attr("r", function(d){return d.value;})
    .style("fill", function(d){return d.color;});

  u.exit().remove();
}
```
https://jsbin.com/qixejuy/edit?html,js,console,output



[Page 4](page4.md)