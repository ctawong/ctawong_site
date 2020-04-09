---
layout: projects
title: Projects
permalink: /projects/
---
## Projects

<table style="width:80%" border="0">
{%- for post in site.posts -%}
  <tr>
    {%- if post.categories contains 'project'  -%}
    <td>
    <a href = "{{ post.url}}">
    <img src="{{post.icon}}" width="100" height="100">
    </a>
    </td>
    
    <td>{{post.excerpt}}</td>
    {%- endif -%} 
  </tr>
{%- endfor -%}   

</table>
