---
layout: page
title:  Wilson Lab
subtitle: Gale and Ira Drukier Institute for Children’s Health <br> Weill Cornell Medicine
cover-img:
  - "./img/wcm.png"
---

<h2>What we do</h2>

Antibodies are critical for adaptive immunity and represent the primary correlate of protection for most vaccines. They are also an important type of therapeutic with rapidly growing demand.

We utilize various technologies and approaches to study autoimmunity, B cell biology, and immune responses to infectious diseases in humans and mice, with a special focus on influenza vaccinology. The Wilson laboratory typically investigates B cell questions from a "specificity-first” perspective by characterizing B cell and monoclonal antibody specificities to interpret immune responses or assess B cell tolerance. Our recent work has involved extensive use of single-cell transcriptomics combined with cell surface and antigen-binding techniques using oligonucleotide hash-tagging. We then employ multiple methods and technologies to further characterize the B cells and antibodies involved in these responses. 

<h2>Activities</h2>

<p>
 <a class="twitter-timeline"
 href="https://twitter.com/patwilsonlab1"
 data-widget-id="340639437736255489"
 data-chrome="nofooter noborders transparent" data-tweet-limit="3"> Find me on X (formerly Twitter) @PatWilsonLab1</a>
 <script>
						!function(d, s, id) {
							var js, fjs = d.getElementsByTagName(s)[0], p = /^http:/
									.test(d.location) ? 'http' : 'https';
							if (!d.getElementById(id)) {
								js = d.createElement(s);
								js.id = id;
								js.src = p
										+ "://platform.twitter.com/widgets.js";
								fjs.parentNode.insertBefore(js, fjs);
							}
						}(document, "script", "twitter-wjs");
 </script>
</p>

<h2>News</h2>

{% assign posts = paginator.posts | default: site.posts %}

<div class="posts-list">
  {% for post in posts %}
  <article class="post-preview">

    {%- capture thumbnail -%}
      {% if post.thumbnail-img %}
        {{ post.thumbnail-img }}
      {% elsif post.cover-img %}
        {% if post.cover-img.first %}
          {{ post.cover-img[0].first.first }}
        {% else %}
          {{ post.cover-img }}
        {% endif %}
      {% else %}
      {% endif %}
    {% endcapture %}
    {% assign thumbnail=thumbnail | strip %}

    {% if site.feed_show_excerpt == false %}
    {% if thumbnail != "" %}
    <div class="post-image post-image-normal">
      <a href="{{ post.url | absolute_url }}" aria-label="Thumbnail">
        <img src="{{ thumbnail | absolute_url }}" alt="Post thumbnail">
      </a>
    </div>
    {% endif %}
    {% endif %}

    <a href="{{ post.url | absolute_url }}">
      <h2 class="post-title">{{ post.title }}</h2>

      {% if post.subtitle %}
        <h3 class="post-subtitle">
        {{ post.subtitle }}
        </h3>
      {% endif %}
    </a>

    <p class="post-meta">
      {% assign date_format = site.date_format | default: "%B %-d, %Y" %}
      Posted on {{ post.date | date: date_format }}
    </p>

    {% if thumbnail != "" %}
    <div class="post-image post-image-small">
      <a href="{{ post.url | absolute_url }}" aria-label="Thumbnail">
        <img src="{{ thumbnail | absolute_url }}" alt="Post thumbnail">
      </a>
    </div>
    {% endif %}

    {% unless site.feed_show_excerpt == false %}
    {% if thumbnail != "" %}
    <div class="post-image post-image-short">
      <a href="{{ post.url | absolute_url }}" aria-label="Thumbnail">
        <img src="{{ thumbnail | absolute_url }}" alt="Post thumbnail">
      </a>
    </div>
    {% endif %}

    <div class="post-entry">
      {% assign excerpt_length = site.excerpt_length | default: 50 %}
      {{ post.excerpt | strip_html | xml_escape | truncatewords: excerpt_length }}
      {% assign excerpt_word_count = post.excerpt | number_of_words %}
      {% if post.content != post.excerpt or excerpt_word_count > excerpt_length %}
        <a href="{{ post.url | absolute_url }}" class="post-read-more">[Read&nbsp;More]</a>
      {% endif %}
    </div>
    {% endunless %}

    {% if site.feed_show_tags != false and post.tags.size > 0 %}
    <div class="blog-tags">
      Tags:
      {% for tag in post.tags %}
      <a href="{{ '/tags' | absolute_url }}#{{- tag -}}">{{- tag -}}</a>
      {% endfor %}
    </div>
    {% endif %}

   </article>
  {% endfor %}
</div>

{% if paginator.total_pages > 1 %}
<ul class="pagination main-pager">
  {% if paginator.previous_page %}
  <li class="page-item previous">
    <a class="page-link" href="{{ paginator.previous_page_path | absolute_url }}">&larr; Newer Posts</a>
  </li>
  {% endif %}
  {% if paginator.next_page %}
  <li class="page-item next">
    <a class="page-link" href="{{ paginator.next_page_path | absolute_url }}">Older Posts &rarr;</a>
  </li>
  {% endif %}
</ul>
{% endif %}
