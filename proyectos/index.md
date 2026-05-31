---
title: "Proyectos"
body_class: "content-page"
---
<p class="has-large-font-size">Proyectos</p>
<p>Este Portfolio es un recorrido de mis últimos años como estudiante de Grado en la Escuela Técnica Superior de Arquitectura ETSAV UPC y Bauhaus Universität y una recopilación de aquellos proyectos que me formaron y me ayudaron a determinar mi camino.</p>

<div class="wp-block-group">
{% assign row_ids = "1,2" | split: "," %}
{% for row_id in row_ids %}
{% assign row_projects = site.data.projects | where: "row", row_id %}
<div class="wp-block-columns{% if row_id == "1" %} alignfull{% endif %}">
{% for project in row_projects %}
<div class="wp-block-column{% if project.column_class %} {{ project.column_class }}{% endif %}"{% if project.column_style %} style="{{ project.column_style }}"{% endif %}>
<figure class="wp-block-image aligncenter size-medium{% if project.image_style %} is-resized{% endif %}{% if project.slug == 'conectar-para-revivir' %} has-custom-border{% endif %}">
<a href="{{ '/proyectos/' | append: project.slug | append: '/' | relative_url }}"><img src="{{ project.thumbnail | relative_url }}" alt="" class="{{ project.image_class }}"{% if project.image_style %} style="{{ project.image_style }}"{% endif %}{% if project.width %} width="{{ project.width }}"{% endif %}{% if project.height %} height="{{ project.height }}"{% endif %}/></a>
<figcaption class="wp-element-caption">{{ project.caption_prefix }}<a href="{{ '/proyectos/' | append: project.slug | append: '/' | relative_url }}">{{ project.title }}</a></figcaption>
</figure>
{% if project.slug == 'recuperar-el-horizonte' %}<p></p>{% endif %}
</div>
{% endfor %}
</div>
{% endfor %}
</div>
