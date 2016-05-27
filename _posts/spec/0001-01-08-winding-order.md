---
layout: redirect
redirect: /vector-tiles/specification/
title: Winding order
hash: winding-order
category: specification
---

Winding order refers to the direction a ring is drawn in a vector tile, either clockwise or counter-clockwise. Many geometries are multipolygons with "holes," which are also represented as polygon rings. It is important to be able to infer winding order to extract source data from a vector tile and understand if the geometry is part of a multipolygon or a unique polygon.

Extracting the original data from images has been difficult on maps in the past, because of the loss of underlying metadata from the geometry that might have been used to create the image. However, with the introduction of client side rendering of vector tiles via GL technologies, the raw geometry data has become useful suddenly for a source of information outside of just rendering.

In order for renderers to appropriately distinguish which polygons are holes and which are unique geometries, the specification requires all polygons to be valid ([OGC validity](http://www.opengeospatial.org/standards/sfa)). Any polygon interior ring must be oriented with the winding order opposite that of their parent exterior ring and all interior rings must directly follow the exterior ring to which they belong. Exterior rings must be oriented clockwise and interior rings must be oriented counter-clockwise (when viewed in screen coordinates).

The following example geometries show how encoding a ring's winding order can affect the rendered result. Each example assumes all rings are part of the same multipolygon.

<div id="js-example-encoding" class="js-example clearfix">
  <div class="js-example-body">
    <div class="wo-block col12 clearfix">
      <div class="col6 pad1"><strong>Description</strong></div>
      <div class="col3 pad1" style="text-align: center;"><strong>Winding order</strong></div>
      <div class="col3 pad1" style="text-align: center;"><strong>Rendered</strong></div>
    </div>
    <div class="wo-block col12 clearfix">
      <div class="col6 pad1">
        <p>A single ring, in clockwise order is rendered as a single, solid polygon.</p>
        <pre><code>Ring 1: Clockwise</code></pre>
      </div>
      <div class="col3 pad1 rotating-rings">
        <img src="{{site.baseurl}}/images/cw.png" class="ring outer cw">
      </div>
      <div class="col3 pad1">
        <img src="{{site.baseurl}}/images/wo-1.png" class="render">
      </div>
    </div>
    <div class="wo-block col12 clearfix">
      <div class="col6 pad1">
        <p>Two rings with the same winding order will render as two unique polygons overlapping.</p>
        <pre><code>Ring 1: Clockwise
Ring 2: Clockwise</code></pre></div>
      <div class="col3 pad1 rotating-rings">
        <img src="{{site.baseurl}}/images/cw.png" class="ring outer cw">
        <img src="{{site.baseurl}}/images/cw.png" class="ring inner cw">
      </div>
      <div class="col3 pad1">
        <img src="{{site.baseurl}}/images/wo-2.png" class="render">
      </div>
    </div>
    <div class="wo-block col12 clearfix">
      <div class="col6 pad1">
      <p>Two rings, the first (exterior) ring is in clockwise order, while the second is counter-clockwise. This results in a "hole" in the final render.</p>
      <pre><code>Ring 1: Clockwise
Ring 2: Counter-Clockwise</code></pre></div>
      <div class="col3 pad1 rotating-rings">
        <img src="{{site.baseurl}}/images/cw.png" class="ring outer cw">
        <img src="{{site.baseurl}}/images/ccw.png" class="ring inner ccw">
      </div>
      <div class="col3 pad1">
        <img src="{{site.baseurl}}/images/wo-3.png" class="render">
      </div>
    </div>
    <div class="wo-block col12 clearfix">
      <div class="col6 pad1">
        <p>Partially overlapping rings in a multipolygon with different winding orders. The second, counter-clockwise ring will be filled outside of the polygon, but not within. This is a result of <strong>even-odd filling</strong> style.</p>
        <pre><code>Ring 1: Clockwise
Ring 2: Counter-Clockwise</code></pre>
      </div>
      <div class="col3 pad1 rotating-rings">
        <img src="{{site.baseurl}}/images/cw.png" class="ring outer left cw">
        <img src="{{site.baseurl}}/images/ccw.png" class="ring inner right ccw">
      </div>
      <div class="col3 pad1">
        <img src="{{site.baseurl}}/images/wo-4.png" class="render">
      </div>
    </div>
    <div class="wo-block col12 clearfix">
      <div class="col6 pad1">
        <p>Three rings in a multipolygon that alternate winding order.</p>
        <pre><code>Ring 1: Clockwise
Ring 2: Counter-Clockwise
Ring 3: Clockwise</code></pre>
      </div>
      <div class="col3 pad1 rotating-rings">
        <img src="{{site.baseurl}}/images/cw.png" class="ring outer cw">
        <img src="{{site.baseurl}}/images/ccw.png" class="ring inner left ccw">
        <img src="{{site.baseurl}}/images/cw.png" class="ring outer small cw">
      </div>
      <div class="col3 pad1">
        <img src="{{site.baseurl}}/images/wo-5.png" class="render">
      </div>
    </div>
  </div>
</div>

