---
layout: redirect
redirect: /vector-tiles/specification/
title: Encoding geometry
hash: encoding-geom
category: specification
---

To encode geographic information into a vector tile a tool must convert geographic coordinates, such as latitude and longitude, into vector tile grid coordinates. Vector tiles hold no concept of geographic information. They encode points, lines, and polygons as `x`/`y` pairs relative to the top left of the grid in a right-down manner.

This is a step-by-step example showing how a single vector tile encodes geometry in the grid. It follows the commands of the "pen" to encode two rings.

<div id="js-example-encoding" class="js-example clearfix bleed-section">
  <div class="js-example-body">
    <div id="vt-info" class="col6 pad1x">
      <button id="vt-next" class="button fill-green rcon next fr">Next step</button>
      <h4 id="vt-title">Step 0</h4>
      <p id="vt-command">An empty vector tile</p>
      <p id="vt-description">The vector tile to the left is a 10x10 grid with 2 cell buffer. Let's encode some geometry to the grid. Let's start with the <span class="poly blue">blue polygon</span>.</p>
    </div>
    <div id="visuals" class="col3">
      <h4>Vector Tile Grid</h4>
      <canvas id="grid"></canvas>
    </div>
    <div class="col3">
      <h4>Commands</h4>
      <pre><code id="vt-command-steps"></code></pre>
    </div>
  </div>
</div>

<div id="js-example-encoding2" class="js-example clearfix">

</div>

### How are geometry clipped?

Geometry clipping is not considered part of this specification. 

<script src="{{site.baseurl}}/js/site.js"></script>