---
layout: home
title: B. L. Escobar
subtitle: Thrilling books set in the dirty, grim, overcrowded far future.
cover-img: "/assets/img/covers/1.jpg"
---

# Want a Free Short Story?

The best introduction to my writing is **"The Promotion"**, a short story set in the world of Decorat. Good news is, you can get it for free!

Just subscribe to my newsletter below.

{% include newsletter-magnet-the-promotion.html %}

{% assign books = site.pages | where_exp: "item" , "item.path contains 'books'"%}

<div class="book-list">
<h1>My Books!</h1>
<div class="book-series-container">
{% for book in books %}
{%- capture thumbnail -%}
      {% if book.thumbnail-img %}
        {{ book.thumbnail-img }}
      {% elsif book.cover-img %}
        {% if book.cover-img.first %}
          {{ book.cover-img[0].first.first }}
        {% else %}
          {{ book.cover-img }}
        {% endif %}
      {% endif %}
{% endcapture %}
{% assign thumbnail=thumbnail | strip %}

    <section class="book-in-series">
    
    <a href="{{ book.url | absolute_url }}" aria-label="Thumbnail">
        <img src="{{ thumbnail | absolute_url }}" alt="Post thumbnail">
    </a>
                    
    {% assign cta_url=book.action-link %}
    {% assign cta_text=book.action-text %}
    {% include cta-button.html target=cta_url title=cta_text %}
    </section>

{% endfor %}
</div>
