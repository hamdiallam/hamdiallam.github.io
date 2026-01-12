---
layout: default
---

# Hamdi Allam
<p class="links"><a href="https://github.com/hamdiallam">GitHub</a> · <a href="https://twitter.com/allam_hamdi">Twitter</a> · <a href="https://linkedin.com/in/hamdiallam">LinkedIn</a></p>

{% for post in site.posts %}
<div class="post-item">
<small>{{ post.date | date: "%B %-d, %Y" }}</small>
<h3><a href="{{ post.url }}">{{ post.title }}</a></h3>
</div>
{% endfor %}
