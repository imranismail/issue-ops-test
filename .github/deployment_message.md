{% set deploymentType = " **noop** " if noop else " " %}
{% set emoji = "⚠️" %}
{% set message = ["Warning:", deploymentType, "diffing status is unknown, please use caution"] %}
{% if status === "success" -%}
  {% set emoji = "✅" %}
  {% set message = ["**", actor, "**", " successfully", deploymentType, "diffed branch `", ref, "` to **", environment, "**"] %}
{%- elif status === "failure" -%}
  {% set emoji = "❌" %}
  {% set message = ["**", actor, "**", " had a failure when", deploymentType, "diffing branch `", ref, "` to **", environment, "**"] %}
{%- endif %}

### Diff Results {{ emoji }}

{{ message | join }}
