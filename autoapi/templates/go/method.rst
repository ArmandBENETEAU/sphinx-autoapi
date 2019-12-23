Method: {{ obj.name }}
*****************************

{# Creating the parameters line #}
{% set ns = namespace(tmpstring='') %}
{% set argjoin = joiner(', ') %}
{% for param in obj.parameters %}
    {% set ns.tmpstring = ns.tmpstring ~ argjoin() ~ param.name ~ ' ' ~ param.type %}
{% endfor %}

.. {{ obj.ref_type }}:: {{ obj.name }}({{ ns.tmpstring }})


{% macro render() %}{{ obj.docstring }}{% endmacro %}
{{ render()|indent(3) }}

{# Don't define parameter description here, that can be done in the block
above #}