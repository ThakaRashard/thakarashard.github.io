

{% highlight javascript %}
{% assign image_files = site.static_files | where: "image", true %}
{% for myimage in image_files %}
  {{ myimage.path }}
{% endfor %}
{% endhighlight %}

<style>
#content {

background: linear-gradient(
    45deg,
    #08a0e9 25%,
    #e8f5fd 0,
    #e8f5fd 50%,
    #08a0e9 0,
    #08a0e9 75%,
    #e8f5fd 0
  );
  background-size: 80.4px 80.4px;
  font-family: "VT323", monospace;
  background-attachment: fixed;


}
    table.blueTable {
  border: 1px solid #1C6EA4;
  background-color: #EEEEEE;
  width: 100%;
  text-align: left;
  border-collapse: collapse;
}
table.blueTable td, table.blueTable th {
  border: 1px solid #AAAAAA;
  padding: 3px 2px;
}
table.blueTable tbody td {
  font-size: 13px;
  color: #333333;
}
table.blueTable tr:nth-child(even) {
  background: #D0E4F5;
}
table.blueTable thead {
  background: #1C6EA4;
  background: -moz-linear-gradient(top, #5592bb 0%, #327cad 66%, #1C6EA4 100%);
  background: -webkit-linear-gradient(top, #5592bb 0%, #327cad 66%, #1C6EA4 100%);
  background: linear-gradient(to bottom, #5592bb 0%, #327cad 66%, #1C6EA4 100%);
  border-bottom: 2px solid #444444;
}
table.blueTable thead th {
  font-size: 15px;
  font-weight: bold;
  color: #FFFFFF;
  border-left: 2px solid #D0E4F5;
}
table.blueTable thead th:first-child {
  border-left: none;
}

table.blueTable tfoot {
  font-size: 14px;
  font-weight: bold;
  color: #FFFFFF;
  background: #D0E4F5;
  background: -moz-linear-gradient(top, #dcebf7 0%, #d4e6f6 66%, #D0E4F5 100%);
  background: -webkit-linear-gradient(top, #dcebf7 0%, #d4e6f6 66%, #D0E4F5 100%);
  background: linear-gradient(to bottom, #dcebf7 0%, #d4e6f6 66%, #D0E4F5 100%);
  border-top: 2px solid #444444;
}
table.blueTable tfoot td {
  font-size: 14px;
}
table.blueTable tfoot .links {
  text-align: right;
}
table.blueTable tfoot .links a{
  display: inline-block;
  background: #1C6EA4;
  color: #FFFFFF;
  padding: 2px 8px;
  border-radius: 5px;
}
</style>

![normani](https://pbs.twimg.com/media/GMM-5OdakAAy7aK?format=jpg&name=large) [Scrollbar styling: scrollbar-color](https://codepen.io/ricoThaka/pen/poBBvgw?editors=1100)
## parse 

<content>

![normani](https://pbs.twimg.com/media/GMM-5OdakAAy7aK?format=jpg&name=large) [Scrollbar styling: scrollbar-color](https://codepen.io/ricoThaka/pen/poBBvgw?editors=1100)
## parse 


<table class="blueTable">
<thead>
<tr>
<th>head1</th>
<th>head2</th>
<th>head3</th>
<th>head4</th>
</tr>
</thead>
<tfoot>
<tr>
<td colspan="4">
<div class="links"><a href="#">&laquo;</a> <a class="active" href="#">1</a> <a href="#">2</a> <a href="#">3</a> <a href="#">4</a> <a href="#">&raquo;</a></div>
</td>
</tr>
</tfoot>
<tbody>
<tr>
<td>cell1_1</td><td>cell2_1</td><td>cell3_1</td><td>cell4_1</td></tr>
<tr>
<td>cell1_2</td><td>cell2_2</td><td>cell3_2</td><td>cell4_2</td></tr>
<tr>
<td>cell1_3</td><td>cell2_3</td><td>cell3_3</td><td>cell4_3</td></tr>
<tr>
<td>cell1_4</td><td>cell2_4</td><td>cell3_4</td><td>cell4_4</td></tr>
</tbody>
</tr>
</table>
</content>