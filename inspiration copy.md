---
layout: journalindex
subtitle: 
use-site-title: true
---

<div class="c-post-list">
  

  <div class="c-post-list__posts c-post-list__posts--beta" style="border-top: none;">

    {% for post in site.tags.work %}

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



    
      <div class="dev-readmore">
      <a
        class="o-btn o-btn--decorative" id="load-more"
        onclick="window.track.interactions('Journal', 'Load more posts', this)">
        <span>
         Prev Page
        </span>
      </a>
      <a
        class="o-btn o-btn--decorative" id="load-more"
        onclick="window.track.interactions('Journal', 'Load more posts', this)">
        <span>
         Next Page
        </span>
      </a>
    </div>
    
  </div>

 
</div>




  
                    
