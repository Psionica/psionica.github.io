---
layout: default
title: Thoughtware
nav_order: 3
description: "A discovery hub for innovative tools for thought."
---

# Thoughtware Discovery Hub
{: .fs-9 .mt-0 }

A curated repository of innovative tools for thought to make use of today.
{: .fs-6 .fw-300 .text-left }

[Submit Tool](https://forms.gle/Y3oejDyLoHbw3Ytn9){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 } [Tweet This](https://twitter.com/home?status=Psionica's%20moving%20from%20a%20portfolio%20of%20its%20own%20to%20a%20discovery%20hub%20for%20innovative%20thoughtware%20at%20large.%20Each%20listed%20tool%20introduces%20new%20mechanics%20%2F%20primitives%20%2F%20affordances.%20%20Skim%20through%20the%20tools%20and%20submit%20your%20own%3A%20https%3A%2F%2Fpsionica.org%2Fthoughtware){: .btn .fs-5 .mb-4 .mb-md-0 }

Each tool listed below introduces new mechanics, primitives, or affordances which can be broadly used in knowledge work. This platform aims to encourage creative individuals and small teams to bring innovative tools for thought to life.

---

{% for tool in site.thoughtware %}
<div class="card">
    <div class="card-body">
        <h2>
            {{ tool.title }}
        </h2>
        <p>
            By {{ tool.author }}
        </p>
        <p>
            {% if tool.os %}
                <div class="label label-green" style="margin: 5px; margin-top: 0; margin-bottom: 0">
                    open source
                </div>
            {% endif %}
            {% for tag in tool.tags %}
                <div class="label" style="margin: 5px; margin-top: 0; margin-bottom: 0">
                    {{ tag }}
                </div>
            {% endfor %}
        </p>
        <p>
            <b>
                Description:
            </b>
            {{ tool.description }}
        </p>
        <p>
            <b>
                New mechanics:
            </b>
            {{ tool.mechanics }}
        </p>
        {{ tool.content }}
    </div>
</div>
{% endfor %}