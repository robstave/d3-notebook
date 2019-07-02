# Joining Data

Data can be joined to the elements in the dom with the data call.

See 
https://jsbin.com/mevosok/edit?html,js,output

In this case we have the code

'''

var data1 = [
  { value: 33},
  { value: 22},
  { value: 11},
  { value: 9},
   
];


function joinData1() {
	d3.selectAll('g.item circle')
    .data(data1)
    .attr('r', function(d){
      return d.value
    })
  
}
'''

The select all returns the selection of 4 elements and the data call joins the data to the elements.  Function calls from that point on will refer to "d" as the data.  In this case, the value of the data will determine "r".


[https://www.d3indepth.com/datajoins/](https://www.d3indepth.com/datajoins/) goes a little more in depth here. 

Use the Inspector to see the data acually attached to the DOM.

[Page 3](page3.md)


