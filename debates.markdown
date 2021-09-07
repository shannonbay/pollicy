---
layout: page
title: Debates
permalink: /debates/
---

Version controlled crowd-sourced A/B tested debate platform

Pollicy is a new thing. An open-source search for truth; a platform for fair and balanced discussion without the noise, ego and narrative control.  Explore and update a versioned debate.  Mind-map of statements which support, oppose or rebut the moot, complete with citations! 
* All statements are explicitly tagged as positive (factual, objective, descriptive) or normative (opinion, subjective or values-based).
* Every change is committed to the repository, but must pass A/B polling to confirm it enhances the debate.  An unpopular new sentiment only needs 30% upvotes to enter the main branch, while edits require  60% or more.
* Anyone may create a new debate or even clone an existing one.  Pollicy continually scans github for new debates to list in it's explorer.

This is the base Jekyll theme. You can find out more info about customizing your Jekyll theme, as well as basic Jekyll usage documentation at [jekyllrb.com](https://jekyllrb.com/)

You can find the source code for Minima at GitHub:
[jekyll][jekyll-organization] /
[minima](https://github.com/jekyll/minima)

You can find the source code for Jekyll at GitHub:
[jekyll][jekyll-organization] /
[jekyll](https://github.com/jekyll/jekyll)


[jekyll-organization]: https://github.com/jekyll

<div id="repos">
    <div class="container">
        <!-- Filter controls -->
        <div class="field">
            <p class="control has-icons-left">
                <input class="search input" type="text" placeholder="Search repo names">
                <span class="icon is-left">
                    <i class="fas fa-search" aria-hidden="true"></i>
                </span>
            </p>
        </div>
    </div>

    <br>
    <br>

    <div class="container">
        <div id="repo-cards" class="columns is-multiline list">
            {% for repo_data in site.data.all_repos %}
                {% assign repo = repo_data[1] %}
                <div class="column is-3-widescreen is-4-desktop is-6-tablet is-8-mobile">
                    {% include repo-card.html %}
                </div>
            {% endfor %}
        </div>
    </div>

</div>

<script>
        var options = {
            valueNames: [
                {
                    name: 'list-name',
                    attr: 'data-name'
                }
            ]
        };
        var userList = new List('repos', options);

</script>

<div id="cy"/>

<script type="module">
import cytoscape from "{{ site.baseurl }}{% link assets/js/cytoscape.esm.min.js %}"; //./assets/js/cytoscape.esm.min.js";
var cy = cytoscape({

  container: document.getElementById('cy'), // container to render in

  elements: [ // list of graph elements to start with
    { // node a
      data: { id: 'a' }
    },
    { // node b
      data: { id: 'b' }
    },
    { // edge ab
      data: { id: 'ab', source: 'a', target: 'b' }
    }
  ],

  style: [ // the stylesheet for the graph
    {
      selector: 'node',
      style: {
        'background-color': '#666',
        'label': 'data(id)'
      }
    },

    {
      selector: 'edge',
      style: {
        'width': 3,
        'line-color': '#ccc',
        'target-arrow-color': '#ccc',
        'target-arrow-shape': 'triangle',
        'curve-style': 'bezier'
      }
    }
  ],

  layout: {
    name: 'grid',
    rows: 1
  }

});
</script>
