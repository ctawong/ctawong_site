---
layout: articles
title: Articles
permalink: /articles
---
## Articles
<div class="home">



  {%- if site.posts.size > 0 -%}
    <ul class="post-list">
      {%- for post in site.posts -%}

      
      <li>
	        {%- assign date_format = site.minima.date_format | default: "%b %-d, %Y" -%}
	 <!--       <span class="post-meta">{{ post.date | date: date_format }}</span> -->
    	    <h5>
        	  <a class="post-link" href="{{ post.url | relative_url }}">
            	{{ post.title | escape}}
       	   </a>
        	  <span class="post-meta">in {{post.categories}} </span>
     	   </h5>
        	  {{ post.excerpt }}
    	  </li>

      {%- endfor -%}
    </ul>

    <p class="rss-subscribe">subscribe <a href="{{ "/feed.xml" | relative_url }}">via RSS</a></p>
  {%- endif -%}

</div>
