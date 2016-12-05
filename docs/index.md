---
layout: default
---

# Welcome To The Project

The Ag Sensor documentation project tests the github pages documentation for a github repo.
This site hosts all files and resources related to the **Agricultural Multi-Sensor Nodal Network with Mesh Network Wireless Communication Topology** project. 

*Below* are the design teams portfolios, click their names to learn more. *Above* to the upper right is the documentation for the various stages of project development. 

Lastly the **about** page describes the process for this site to be updated and maintained. 


<div class="home">

  <h1 class="page-heading">SME Information</h1>

  <ul class="post-list">
    {% for post in site.posts %}
      <li>
        <span class="post-meta">{{ post.date | date: "%b %-d, %Y" }}</span>

        <h2>
          <a class="post-link" href="{{ post.url | prepend: site.baseurl }}">{{ post.title | escape }}</a>
        </h2>
      </li>
    {% endfor %}
  </ul>

  <p class="rss-subscribe">subscribe <a href="{{ "/feed.xml" | prepend: site.baseurl }}">via RSS</a></p>
  <p class="post-date">Published: {{ 'now' | date: "%x %X" }} UTC</p>
</div>
