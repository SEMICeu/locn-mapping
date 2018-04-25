<h1>SPARQL implementation of the LOCN mappings to vCard and Schema.org</h1>
<p>This folder includes a set of <code>.rq</code> files, specifying a tentative implementation of the mappings defined in DCAT-AP+Schema.org, in the form of <a target="_blank" href="https://www.w3.org/TR/sparql11-query/#construct">SPARQL <code>CONSTRUCT</code> queries</a>.</p>
<p>The mappings have been defined in a modular way, with a separate SPARQL query for each of the LOCN classes, and related properties. A complete representation of a given resource (e.g., an address) and related resource (e.g., the address point geometry) can be obtained by combining the relevant SPARQL queries.</p>
<h2>LOCN to vCard mappings</h2>
<ul>
<li><a href="./Address-locn-to-vcard.rq"><code>Address-locn-to-vcard.rq</code></a>: Mappings for class <code>locn:Address</code> and related properties</li>
<li><a href="./geographicName-locn-to-vcard.rq"><code>geographicName-locn-to-vcard.rq</code></a>: Mappings for property <code>locn:geographicName</code></li>
<li><a href="./geometry-locn-to-vcard.rq"><code>geometry-locn-to-vcard.rq</code></a>: Mappings for property <code>locn:geometry</code></li>
<li><a href="./Geometry-locn-to-vcard.rq"><code>Geometry-locn-to-vcard.rq</code></a>: Mappings for class <code>locn:Geometry</code> and related properties</li>
</ul>
<h2>LOCN to Schema.org mappings</h2>
<ul>
<li><a href="./Address-locn-to-schema-org.rq"><code>Address-locn-to-schema-org.rq</code></a>: Mappings for class <code>locn:Address</code> and related properties</li>
<li><a href="./geographicName-locn-to-schema-org.rq"><code>geographicName-locn-to-schema-org.rq</code></a>: Mappings for property <code>locn:geographicName</code></li>
<li><a href="./geometry-locn-to-schema-org.rq"><code>geometry-locn-to-schema-org.rq</code></a>: Mappings for property <code>locn:geometry</code></li>
<li><a href="./Geometry-locn-to-schema-org.rq"><code>Geometry-locn-to-schema-org.rq</code></a>: Mappings for class <code>locn:Geometry</code> and related properties</li>
</ul>


