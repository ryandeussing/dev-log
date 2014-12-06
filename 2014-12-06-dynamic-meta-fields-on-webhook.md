Use custom meta fiels when it exists, else fallback to site meta field:

    {% set meta = getSetting('site_description')%}
      {% extends "templates/partials/base.html" %}
        {% block description %}{{ item.meta|default(meta) }}{% endblock %}