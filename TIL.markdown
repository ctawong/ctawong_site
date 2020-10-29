---
layout: page
title: TIL
permalink: /TIL/
datatable: true
---

{% assign row = site.data.TIL[0] %}
<script type="text/javascript" language="javascript" src="https://code.jquery.com/jquery-3.5.1.js"></script>
<script type="text/javascript" language="javascript" src="https://cdn.datatables.net/1.10.22/js/jquery.dataTables.min.js"></script>
<script>
$(document).ready(function() {
    $('#til_table').DataTable({
    "paging": false,
     "order": [[ 0, "desc" ]]
    });
} );
</script>

<table class="display" id="til_table" style="width:100%">
<thead>
<tr> 
<th> date </th>
<th> category </th>
<th> content </th>
</tr>
</thead>
<tbody>
{% for row in site.data.TIL %}
{% if row.first %}  <!-- display only non-empty lines -->

	<tr>
	<td> {{row['date']}} </td>
	<td> {{row['category']}} </td>
	<td markdown="span"> {{row['content']}} </td>	
	</tr>
{% endif %}
{% endfor %} 
</tbody>
</table>