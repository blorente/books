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

<div class="posts-list">
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
    <article class="post-preview">
        <div class="post-image post-image-normal">
            <a href="{{ book.url | absolute_url }}" aria-label="Thumbnail">
                <img src="{{ thumbnail | absolute_url }}" alt="Post thumbnail">
            </a>
        </div>
        <a href="{{ book.url | absolute_url }}">
        <h2 class="post-title">{{ book.title | strip_html }}</h2>

        {% if book.subtitle %}
            <h3 class="book-subtitle">
            {{ book.subtitle | strip_html }}
            </h3>
        {% endif %}
        </a>
    <br>
    {% assign target_url=book.url %}
    {% include cta-button.html target=target_url title="Read More" %}

</article>
{% endfor %}
</div>
