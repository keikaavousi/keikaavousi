---
layout: default
title: Blog
permalink: /blog/
---

<main class="blog-page">
    <header class="blog-header">
        <h1>Blog</h1>
        <p>Notes on software, AI, and things I'm learning.</p>
    </header>

    {% if site.posts.size > 0 %}
    <ul class="blog-list">
        {% for post in site.posts %}
        <li class="blog-list-item">
            <a class="blog-post-title" href="{{ post.url | relative_url }}">{{ post.title }}</a>
            <p class="blog-post-meta">{{ post.date | date: "%B %-d, %Y" }}</p>
            {% if post.excerpt %}
            <p class="blog-post-excerpt">{{ post.excerpt | strip_html | truncate: 180 }}</p>
            {% endif %}
        </li>
        {% endfor %}
    </ul>
    {% else %}
    <p>No posts yet.</p>
    {% endif %}

    <p class="post-back"><a href="{{ '/' | relative_url }}">← Back to home</a></p>

</main>
