---
layout: journalindex
subtitle:
use-site-title: true
---
<div class="c-post-list">


  <div class="c-post-list__posts c-post-list__posts--beta" style="border-top: none;">
{% assign numPosts = site.posts | size %}
{% if numPosts == 0 %}
    <p>No posts...yet. Working on it please check back soon 🙂 </p>
{% endif %}


    {% for post in site.posts %}

  <a class="c-post-list__post" href="{{ post.url | prepend: site.baseurl }}" title="">
       {% if post.image %}
        <img
          src="{{ post.image }}"
          alt=""
          data-aos="grayscale">
        {% endif %}
        <h2 class="">{{ post.title }}</h2>
             <span><p>{{ post.excerpt | strip_html | truncatewords:50 }}  </p></span>
</a>



  {% endfor %}



     {% if paginator.total_pages > 1 %}
<div class="dev-readmore">
    {% if paginator.previous_page %}

        <a href="{{ paginator.previous_page_path | prepend: site.baseurl | replace: '//', '/' }}" class="o-btn o-btn--decorative" id="load-more">
        <span> Prev Page </span>
      </a>
  {% endif %}

  {% if paginator.next_page %}

               <a class="o-btn o-btn--decorative" id="load-more" href="{{ paginator.next_page_path | prepend: site.baseurl | replace: '//', '/' }}">
               <span>Next Page </span>
               </a>
  {% endif %}
</div>
{% endif %}

  </div>


</div>
