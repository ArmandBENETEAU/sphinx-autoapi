Type: {{ obj.name }}
''''''''''''''''''''''''''

.. go:{{ obj.ref_type }}:: {{ obj.name }}

{% macro render() %}{{ obj.docstring }}{% endmacro %}
{{ render() }}

{% if obj.children %}
    {% for child in obj.children|sort %}
{% macro render_child() %}{{ child.render() }}{% endmacro %}
{{ render_child() }}
    {% endfor %}
{% endif %}

