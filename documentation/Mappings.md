<article>
<header>
<h1>LOCN mappings to vCard and Schema.org</h1>
</header>
<section id="abstract">
<h2>Abstract</h2>
<p>This document presents a proposal for mapping the relevant terms from the <a target="_blank" href="http://www.w3.org/ns/locn">ISA Core Location Vocabulary</a> (LOCN) to the <a target="_blank" href="http://www.w3.org/TR/vcard-rdf/">vCard Ontology</a> (vCard) and to the <a target="_blank" href="http://schema.org/">Schema.org vocabulary</a> (Schema.org).</p>
</section>
<section id="sotd">
<h2>Status of this document</h2>
<p>This document is a draft meant to report work in progress. As such, it can be updated any time and it must be considered as unstable.</p>
<p>Comments and queries should be sent to the <a href="https://joinup.ec.europa.eu/asset/core_location/">ISA Core Location Vocabulary Task Force</a> via <a href="mailto:core_location@joinup.ec.europa.eu">core_location@joinup.ec.europa.eu</a>.</p>
</section>
<nav id="toc">
<h2>Table of contents</h2>
<ul>
<li><a href="#background">Background</a></li>
<li><a href="#methodology">Methodology</a></li>
<li><a href="#alignment-issues">Summary of alignment issues</a></li>
<li><a href="#used-namespaces">Used namespaces</a></li>
<li><a href="#mapping-summary">Mapping summary</a></li>
<li><a href="#formal-definition-skos">SKOS definition</a>
<li><a href="#formal-definition-sparql">SPARQL implementation</a>
<ul>
<li><a href="#formal-definition-sparql-locn-2-vcard">LOCN to vCard mapping</a></li>
<li><a href="#formal-definition-sparql-locn-2-schema.org">LOCN to Schema.org mapping</a></li>
</ul>
</li>
</ul>
</nav>
<section id="background">
<h2><a name="background">Background</a></h2>
<p>The ISA Programme Location Core Vocabulary provides a minimum set of classes and properties for describing any place in terms of its name, address or geometry. The vocabulary is specifically designed to aid the publication of data that is interoperable with <a href="http://inspire.jrc.ec.europa.eu/"><abbr title="European Union">EU</abbr> INSPIRE Directive</a>. It is closely integrated with the <a href="https://joinup.ec.europa.eu/node/42441">Business</a> and <a href="https://joinup.ec.europa.eu/node/42440">Person</a> Core Vocabularies of the EU <abbr title="Interoperability Solutions for European Public Administrations">ISA</abbr> Programme, now available in W3C space as, respectively, the <a href="http://www.w3.org/ns/regorg">Registered Organization vocabulary</a> and <a href="http://www.w3.org/ns/person">ISA Person Core Vocabulary</a>.</p>
<p>This document presents a proposal for mapping the relevant terms from the <a target="_blank" href="http://www.w3.org/ns/locn">ISA Core Location Vocabulary</a> (LOCN) to the <a target="_blank" href="http://www.w3.org/TR/vcard-rdf/">vCard Ontology</a> (vCard) and to the <a target="_blank" href="http://schema.org/">Schema.org vocabulary</a> (Schema.org), which are the two vocabularies most widely used in the Web to represent addresses and location information.</p>
<p>The purpose of this mapping exercise is twofold:</p>
<ol>
<li>Optimise the publication and discovery on the Web of INSPIRE data concerning addresses and location information, by supporting an alternative encoding based on commonly used Web vocabularies.</li>
<li>Enable the sharing and re-use of data concerning addresses and location information expressed by using LOCN, vCard and Schema.org.</li>
</ol>
</section>
<section id="methodology">
<h2><a name="methodology">Methodology</a></h2>
<p>The reference specifications used in this exercise are the following ones:</p>
<ul>
<li><a target="_blank" href="https://www.w3.org/ns/locn">ISA Core Location Vocabulary</a> (<time datetime="2015-03-23">23 March 2015</time>)</li>
<li><a target="_blank" href="https://www.w3.org/TR/2014/NOTE-vcard-rdf-20140522/">vCard Ontology - for describing People and Organizations</a> (<time datetime="2014-05-22">22 May 2014</time>)</li>
<li><a target="_blank" href="http://schema.org/version/2.2/">Schema.org 2.2</a> (<time datetime="2015-11-05">5 November 2015</time>)</li>
</ul>
<p>
<p>For the mappings, existing work has been taken into account concerning the mapping of Schema.org to other metadata standards. In particular:</p>
<ul>
<li><a target="_blank" href="https://github.com/dcmi/schema.org">Schema.org to Dublin Core Map</a> (<time datetime="2011-12-12">12 December 2011</time>)</li>
</ul>
<p>The following sections include:</p>
<ul>
<li>A summary of the mapping issues.</li>
<li>A table providing an overview of the proposed mappings.</li>
<li>A formal definition of the proposed mappings, encoded in the form of SPARQL queries.</li>
</ul>
</section>
<section id="alignment-issues">
<h2><a name="alignment-issues">Summary of alignment issues</a></h2>
<p>The proposed mappings can be grouped into the following classes:</p>
<dl>
<dt><strong>1-to-1 mappings with no mapping issues</strong></dt>
<dd>
<p>This class covers the majority of the mapped terms (9 out of 16).</p>
</dd>
<dt><strong>Many-to-1 mappings</strong></dt>
<dd>
<p>This class includes 2 of the mapped terms, namely, <a target="_blank" title="http://www.w3.org/ns/locn#thoroughfare" href="http://www.w3.org/ns/locn#locn:thoroughfare"><code>locn:thoroughfare</code></a> (street name) and <a target="_blank" title="http://www.w3.org/ns/locn#locatorDesignator" href="http://www.w3.org/ns/locn#locn:locatorDesignator"><code>locn:locatorDesignator</code></a> (street number).</p>
<p>LOCN models this information by using two distinct terms, whereas vCard and Schema.org merge this information into a single property&mdash;namely, <a target="_blank" title="http://www.w3.org/2006/vcard/ns#street-address" href="http://www.w3.org/TR/vcard-rdf/#d4e1218"><code>vcard:street-address</code></a> and <a target="_blank" title="http://schema.org/streetAddress" href="http://schema.org/streetAddress"><code>schema:streetAddress</code></a>, respectively.</p>
<p>This is not an issue when mapping from LOCN to vCard and Schema.org (the two fields are merged into one, preserving all the information). On the other hand, mapping from vCard / Schema.org to LOCN may require further processing to identify the two different components of a street address (namely, street name and number).</p>
</dd>
<dt><strong>Missing mappings</strong></dt>
<dd>
<p>This class includes 4 of the mapped terms, namely, <a target="_blank" title="http://www.w3.org/ns/locn#addressId" href="http://www.w3.org/ns/locn#locn:addressId"><code>locn:addressId</code></a>, <a target="_blank" title="http://www.w3.org/ns/locn#poBox" href="http://www.w3.org/ns/locn#locn:poBox"><code>locn:poBox</code></a>, <a target="_blank" title="http://www.w3.org/ns/locn#locatorName" href="http://www.w3.org/ns/locn#locn:locatorName"><code>locn:locatorName</code></a>, and <a target="_blank" title="http://www.w3.org/ns/locn#addressArea" href="http://www.w3.org/ns/locn#locn:addressArea"><code>locn:addressArea</code></a>.</p>
<p>More precisely:</p>
<ul>
<li><a target="_blank" title="http://www.w3.org/ns/locn#addressId" href="http://www.w3.org/ns/locn#locn:addressId"><code>locn:addressId</code></a> is not supported by Schema.org</li>
<li><a target="_blank" title="http://www.w3.org/ns/locn#poBox" href="http://www.w3.org/ns/locn#locn:poBox"><code>locn:poBox</code></a> is not supported by vCard</li>
<li><a target="_blank" title="http://www.w3.org/ns/locn#locatorName" href="http://www.w3.org/ns/locn#locn:locatorName"><code>locn:locatorName</code></a>, and <a target="_blank" title="http://www.w3.org/ns/locn#addressArea" href="http://www.w3.org/ns/locn#locn:addressArea"><code>locn:addressArea</code></a> are not supported by vCard and Schema.org</li>
</ul>
</dd>
<dt><strong>Mappings with encoding issues</strong></dt>
<dd><p>This class includes 1 of the mapped terms, namely, <a target="_blank" title="http://www.w3.org/ns/locn#geometry" href="http://www.w3.org/ns/locn#locn:geometry"><code>locn:geometry</code></a>.</p>
<p>vCard and Schema.org use specific encodings / representations for geometries, whereas LOCN supports any type of geometry encoding / representation.</p>
<p>This is not an issue when mapping from vCard / Schema.org to LOCN. On the other hand, mapping from LOCN to vCard and Schema.org may require further processing to convert the original geometry encoding / representation to the target one.</p></dd>
</dl>
<p>Based on what said above, the alignments with no severe mapping issues are able to map the following information:</p>
<ul>
<li>The address components most widely used&mdash;namely, street address and number, postal code, locality, region (province or state), country.</li>
<li>The notion of location / place.</li>
<li>Geographic names / toponyms.</li>
</ul>
</section>
<section id="used-namespaces">
<h2><a name="used-namespaces">Used namespaces</a></h2>
<table class="aui">
<thead>
<tr>
<th>Prefix</th>
<th>Namespace URI</th>
<th>Schema &amp; documentation</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>dct</code></td>
<td><code><a href="http://purl.org/dc/terms/">http://purl.org/dc/terms/</a></code></td>
<td><a href="http://dublincore.org/documents/2012/06/14/dcmi-terms/">DCMI Metadata Terms</a></td>
</tr>
<tr>
<td><code>locn</code></td>
<td><code><a href="http://www.w3.org/ns/locn#">http://www.w3.org/ns/locn#</a></code></td>
<td><a href="http://www.w3.org/ns/locn">ISA Programme Core Location Vocabulary</a></td>
</tr>
<tr>
<td><code>schema</code></td>
<td><code><a href="http://schema.org/">http://schema.org/</a></code></td>
<td><a href="http://schema.org/">Schema.org</a></td>
</tr>
<tr>
<td><code>vcard</code></td>
<td><code><a href="http://www.w3.org/2006/vcard/ns#">http://www.w3.org/2006/vcard/ns#</a></code></td>
<td><a href="http://www.w3.org/TR/2013/WD-vcard-rdf-20130924/">vCard Ontology</a></td>
</tr>
</tbody>
</table>
</section>
<section id="mapping-summary">
<h2><a name="mapping-summary">Mapping summary</a></h2>
<p>The following table provides an overview of the proposed mappings between <a target="_blank" href="http://www.w3.org/ns/locn">LOCN</a>, <a target="_blank" href="http://www.w3.org/TR/vcard-rdf/">vCard</a>, and <a target="_blank" href="http://schema.org/">Schema.org</a>.</p>
<table>
<thead>
<tr>
<th>LOCN</th>
<th>vCard</th>
<th>Schema.org</th>
<th>Comments</th>
</tr>
</thead>
<tbody>
<tr>
<td><a target="_blank" title="http://purl.org/dc/terms/Location" href="http://www.w3.org/ns/locn#dcterms:Location"><code>dct:Location</code></a></td>
<td><a target="_blank" title="http://www.w3.org/2006/vcard/ns#Location" href="http://www.w3.org/TR/vcard-rdf/#d4e1865"><code>vcard:Location</code></a></td>
<td><a target="_blank" title="http://schema.org/Place" href="http://schema.org/Place"><code>schema:Place</code></a></td>
<td></td>
</tr>
<tr>
<td><a target="_blank" title="http://www.w3.org/ns/locn#geographicName" href="http://www.w3.org/ns/locn#locn:geographicName"><code>locn:geographicName</code></a></td>
<td><a target="_blank" title="http://www.w3.org/2006/vcard/ns#fn" href="http://www.w3.org/TR/vcard-rdf/#d4e891"><code>vcard:fn</code></a> (<a target="_blank" title="http://www.w3.org/2006/vcard/ns#Location" href="http://www.w3.org/TR/vcard-rdf/#d4e1865"><code>vcard:Location</code></a>)</td>
<td><a target="_blank" title="http://schema.org/fn" href="http://schema.org/d4e891"><code>schema:name</code></a> (<a target="_blank" title="http://schema.org/Place" href="http://schema.org/Place"><code>schema:Place</code></a>)</td>
<td></td>
</tr>
<tr>
<td><a target="_blank" title="http://www.w3.org/ns/locn#geometry" href="http://www.w3.org/ns/locn#locn:geometry"><code>locn:geometry</code></a></td>
<td><a target="_blank" title="http://www.w3.org/2006/vcard/ns#hasGeo" href="http://www.w3.org/TR/vcard-rdf/#d4e239"><code>vcard:hasGeo</code></a></td>
<td><a target="_blank" title="http://schema.org/geo" href="http://schema.org/geo"><code>schema:geo</code></a></td>
<td>
<p>It seems that vCard expects as value a point, encoded as a <a target="_blank" title="IETF RFC 5870 - A Uniform Resource Identifier for Geographic Locations ('geo' URI)" href="http://tools.ietf.org/html/rfc5870.html"><code>geo:</code> URI</a> (<strong>to be verified</strong>).</p>
<p>Schema.org expects as value an instance of <a target="_blank" title="http://schema.org/GeoCoordinates" href="http://schema.org/GeoCoordinates"><code>schema:GeoCoordinates</code></a> (for points) or <a target="_blank" title="http://schema.org/GeoShape" href="http://schema.org/GeoShape"><code>schema:GeoShape</code></a> (for more complex geometries).</p>
<p>LOCN allows any type of geometry, and any type of geometry encoding / representation&mdash;including those supported by vCard and Schema.org.</p>
<p>As a consequence, the <a target="_blank" title="http://www.w3.org/ns/locn#geometry" href="http://www.w3.org/ns/locn#locn:geometry"><code>locn:geometry</code></a> mapping might require further processing to encode the geometry according the encodings / representations supported in vCard and Schema.org.</p>
</td>
</tr>
<tr>
<td rowspan="2"><a target="_blank" title="http://www.w3.org/ns/locn#Geometry" href="http://www.w3.org/ns/locn#locn:Geometry"><code>locn:Geometry</code></a></td>
<td rowspan="2">N/A</td>
<td><a target="_blank" title="http://schema.org/geo" href="http://schema.org/GeoCoordinates"><code>schema:GeoCoordinates</code></a></td>
<td rowspan="2">
<p>See comments on property <code>locn:geometry</code></p>
</td>
</tr>
<tr>
<td><a target="_blank" title="http://schema.org/geo" href="http://schema.org/GeoShape"><code>schema:GeoShape</code></a></td>
</tr>
<tr>
<td><a target="_blank" title="http://www.w3.org/ns/locn#address" href="http://www.w3.org/ns/locn#locn:address"><code>locn:address</code></a></td>
<td><a target="_blank" title="http://www.w3.org/2006/vcard/ns#hasAddress" href="http://www.w3.org/TR/vcard-rdf/#d4e101"><code>vcard:hasAddress</code></a></td>
<td><a target="_blank" title="http://schema.org/address" href="http://schema.org/address"><code>schema:address</code></a></td>
<td></td>
</tr>
<tr>
<td><a target="_blank" title="http://www.w3.org/ns/locn#Address" href="http://www.w3.org/ns/locn#locn:Address"><code>locn:Address</code></a></td>
<td><a target="_blank" title="http://www.w3.org/2006/vcard/ns#Address" href="http://www.w3.org/TR/vcard-rdf/#d4e1292"><code>vcard:Address</code></a></td>
<td><a target="_blank" title="http://schema.org/PostalAddress" href="http://schema.org/PostalAddress"><code>schema:PostalAddress</code></a></td>
<td></td>
</tr>
<tr>
<td><a target="_blank" title="http://www.w3.org/ns/locn#fullAddress" href="http://www.w3.org/ns/locn#locn:fullAddress"><code>locn:fullAddress</code></a></td>
<td><a target="_blank" title="http://www.w3.org/2006/vcard/ns#fn" href="http://www.w3.org/TR/vcard-rdf/#d4e891"><code>vcard:fn</code></a> (<a target="_blank" title="http://www.w3.org/2006/vcard/ns#Address" href="http://www.w3.org/TR/vcard-rdf/#d4e1292"><code>vcard:Address</code></a>)</td>
<td><a target="_blank" title="http://schema.org/name" href="http://schema.org/name"><code>schema:name</code></a> (<a target="_blank" title="http://schema.org/PostalAddress" href="http://schema.org/PostalAddress"><code>schema:PostalAddress</code></a>)</td>
<td></td>
</tr>
<tr>
<td><a target="_blank" title="http://www.w3.org/ns/locn#poBox" href="http://www.w3.org/ns/locn#locn:poBox"><code>locn:poBox</code></a></td>
<td>TBD</td>
<td><a target="_blank" title="http://schema.org/postOfficeBoxNumber" href="http://schema.org/postOfficeBoxNumber"><code>schema:postOfficeBoxNumber</code></a></td>
<td>
<p>vCard includes a specific property, namely, <a target="_blank" title="http://www.w3.org/2006/vcard/ns#post-office-box" href="http://www.w3.org/TR/vcard-rdf/#d4e1110"><code>vcard:post-office-box</code></a>, but its use has been deprecated.</p>
<p>Possible options:</p>
<ol>
<li>leave <a target="_blank" title="http://www.w3.org/ns/locn#poBox" href="http://www.w3.org/ns/locn#locn:poBox"><code>locn:poBox</code></a> unmapped</li>
<li>use <a target="_blank" title="http://www.w3.org/2006/vcard/ns#post-office-box" href="http://www.w3.org/TR/vcard-rdf/#d4e1110"><code>vcard:post-office-box</code></a>, despite it is deprecated</li>
<li>dump it into <a target="_blank" title="http://www.w3.org/2006/vcard/ns#street-address" href="http://www.w3.org/TR/vcard-rdf/#d4e1218"><code>vcard:street-address</code></a></li>
</ol>
</td>
</tr>
<tr>
<td><a target="_blank" title="http://www.w3.org/ns/locn#thoroughfare" href="http://www.w3.org/ns/locn#locn:thoroughfare"><code>locn:thoroughfare</code></a></td>
<td><a target="_blank" title="http://www.w3.org/2006/vcard/ns#street-address" href="http://www.w3.org/TR/vcard-rdf/#d4e1218"><code>vcard:street-address</code></a></td>
<td><a target="_blank" title="http://schema.org/streetAddress" href="http://schema.org/streetAddress"><code>schema:streetAddress</code></a></td>
<td></td>
</tr>
<tr>
<td><a target="_blank" title="http://www.w3.org/ns/locn#locatorDesignator" href="http://www.w3.org/ns/locn#locn:locatorDesignator"><code>locn:locatorDesignator</code></a></td>
<td><a target="_blank" title="http://www.w3.org/2006/vcard/ns#street-address" href="http://www.w3.org/TR/vcard-rdf/#d4e1218"><code>vcard:street-address</code></a></td>
<td><a target="_blank" title="http://schema.org/streetAddress" href="http://schema.org/streetAddress"><code>schema:streetAddress</code></a></td>
<td></td>
</tr>
<tr>
<td><a target="_blank" title="http://www.w3.org/ns/locn#locatorName" href="http://www.w3.org/ns/locn#locn:locatorName"><code>locn:locatorName</code></a></td>
<td>TBD</td>
<td>TBD</td>
<td>
<p>In LOCN, <a target="_blank" title="http://www.w3.org/ns/locn#locatorName" href="http://www.w3.org/ns/locn#locn:locatorName"><code>locn:locatorName</code></a> is defined as follows:</p>
<blockquote>Proper noun(s) applied to the real world entity identified by the locator. The locator name could be the name of the property or complex, of the building or part of the building, or it could be the name of a room inside a building.</blockquote>
<p>vCard includes a specific property, namely, <a target="_blank" title="http://www.w3.org/2006/vcard/ns#extended-address" href="http://www.w3.org/TR/vcard-rdf/#d4e860"><code>vcard:extended-address</code></a>, but its use has been deprecated.</p>
<p>Schema.org does not define terms to model this information.</p>
<p>Possible options:</p>
<ol>
<li>leave <a target="_blank" title="http://www.w3.org/ns/locn#locatorName" href="http://www.w3.org/ns/locn#locn:locatorName"><code>locn:locatorName</code></a> unmapped</li>
<li>use <a target="_blank" title="http://www.w3.org/2006/vcard/ns#extended-address" href="http://www.w3.org/TR/vcard-rdf/#d4e860"><code>vcard:extended-address</code></a>, despite it is deprecated, and leave <a target="_blank" title="http://www.w3.org/ns/locn#locatorName" href="http://www.w3.org/ns/locn#locn:locatorName"><code>locn:locatorName</code></a> unmapped for Schema.org</li>
<li>dump it into <a target="_blank" title="http://www.w3.org/2006/vcard/ns#street-address" href="http://www.w3.org/TR/vcard-rdf/#d4e1218"><code>vcard:street-address</code></a> / <a target="_blank" title="http://schema.org/streetAddress" href="http://schema.org/streetAddress"><code>schema:streetAddress</code></a></li>
</ol>
</td>
</tr>
<tr>
<td><a target="_blank" title="http://www.w3.org/ns/locn#addressArea" href="http://www.w3.org/ns/locn#locn:addressArea"><code>locn:addressArea</code></a></td>
<td>TBD</td>
<td>TBD</td>
<td>
<p>In LOCN, <a target="_blank" title="http://www.w3.org/ns/locn#addressArea" href="http://www.w3.org/ns/locn#locn:addressArea"><code>locn:addressArea</code></a> is defined as follows:</p>
<blockquote>The name or names of a geographic area or locality that groups a number of addressable objects for addressing purposes, without being an administrative unit. This would typically be part of a city, a neighbourhood or village. [&hellip;]</blockquote>
<p>vCard and Schema.org do not define terms to model this information.</p>
<p>Possible options:</p>
<ol>
<li>leave <a target="_blank" title="http://www.w3.org/ns/locn#addressArea" href="http://www.w3.org/ns/locn#locn:addressArea"><code>locn:addressArea</code></a> unmapped</li>
<li>dump it into <a target="_blank" title="http://www.w3.org/2006/vcard/ns#street-address" href="http://www.w3.org/TR/vcard-rdf/#d4e1218"><code>vcard:street-address</code></a> / <a target="_blank" title="http://schema.org/streetAddress" href="http://schema.org/streetAddress"><code>schema:streetAddress</code></a></li>
</ol>
</td>
</tr>
<tr>
<td><a target="_blank" title="http://www.w3.org/ns/locn#postName" href="http://www.w3.org/ns/locn#locn:postName"><code>locn:postName</code></a></td>
<td><a target="_blank" title="http://www.w3.org/2006/vcard/ns#locality" href="http://www.w3.org/TR/vcard-rdf/#d4e999"><code>vcard:locality</code></a></td>
<td><a target="_blank" title="http://schema.org/addressLocality" href="http://schema.org/addressLocality"><code>schema:addressLocality</code></a></td>
<td></td>
</tr>
<tr>
<td><a target="_blank" title="http://www.w3.org/ns/locn#adminUnitL2" href="http://www.w3.org/ns/locn#locn:adminUnitL2"><code>locn:adminUnitL2</code></a></td>
<td><a target="_blank" title="http://www.w3.org/2006/vcard/ns#region" href="http://www.w3.org/TR/vcard-rdf/#d4e1157"><code>vcard:region</code></a></td>
<td><a target="_blank" title="http://schema.org/addressRegion" href="http://schema.org/addressRegion"><code>schema:addressRegion</code></a></td>
<td></td>
</tr>
<tr>
<td><a target="_blank" title="http://www.w3.org/ns/locn#adminUnitL1" href="http://www.w3.org/ns/locn#locn:adminUnitL1"><code>locn:adminUnitL1</code></a></td>
<td><a target="_blank" title="http://www.w3.org/2006/vcard/ns#country-name" href="http://www.w3.org/TR/vcard-rdf/#d4e844"><code>vcard:country-name</code></a></td>
<td><a target="_blank" title="http://schema.org/addressCountry" href="http://schema.org/addressCountry"><code>schema:addressCountry</code></a></td>
<td></td>
</tr>
<tr>
<td><a target="_blank" title="http://www.w3.org/ns/locn#postCode" href="http://www.w3.org/ns/locn#locn:postCode"><code>locn:postCode</code></a></td>
<td><a target="_blank" title="http://www.w3.org/2006/vcard/ns#postal-code" href="http://www.w3.org/TR/vcard-rdf/#d4e1126"><code>vcard:postal-code</code></a></td>
<td><a target="_blank" title="http://schema.org/postalCode" href="http://schema.org/postalCode"><code>schema:postalCode</code></a></td>
<td></td>
</tr>
<tr>
<td><a target="_blank" title="http://www.w3.org/ns/locn#addressId" href="http://www.w3.org/ns/locn#locn:addressId"><code>locn:addressId</code></a></td>
<td><a target="_blank" title="http://www.w3.org/2006/vcard/ns#hasUID" href="http://www.w3.org/TR/vcard-rdf/#d4e592"><code>vcard:hasUID</code></a></td>
<td>TBD</td>
<td>
<p>In vCard, <a target="_blank" title="http://www.w3.org/2006/vcard/ns#hasUID" href="http://www.w3.org/TR/vcard-rdf/#d4e592"><code>vcard:hasUID</code></a> is formally defined as an <code>owl:ObjectProperty</code>, and therefore its value cannot be a literal. However, this seems to be in conflict with its informal definition, which is less restrictive&mdash;quoting:</p>
<blockquote>[&hellip;] a value that represents a globally unique identifier corresponding to the object.</blockquote>
<p>(<strong>to be verified</strong>)</p>
<p>Schema.org does not define terms to model this information.</p>
</td>
</tr>
</tbody>
</table>
</section>
<section id="formal-definition-skos">
<h2><a name="formal-definition-skos">SKOS definition</a></h2>
<p>A tentative SKOS definitions of the mappings is available in a <a href="../skos/">separate folder</a>.</p>
</section>
<section id="formal-definition-sparql">
<h2><a name="formal-definition-sparql">SPARQL implementation</a></h2>
<p>This section illustrates a tentative implementation of the defined mappings, in the form of <a target="_blank" href="https://www.w3.org/TR/sparql11-query/#construct">SPARQL <code>CONSTRUCT</code> queries</a>.</p>
<p>The defined SPARQL queries can be tested on the <a target="_blank" href="http://location.testproject.eu/sparql">SPARQL endpoint</a> of the <a target="_blank" href="http://location.testproject.eu/">ISA Core Location Pilot</a>.</p>
<section id="formal-definition-sparql-locn-2-vcard">
<h3><a name="formal-definition-sparql-locn-2-vcard">LOCN to vCard mapping</a></h3>
<section>
<h4>Mapping rules for <a target="_blank" title="http://www.w3.org/ns/locn#geographicName" href="http://www.w3.org/ns/locn#locn:geographicName"><code>locn:geographicName</code></a></h4>
<p>Test it on the <a target="_blank" href="http://location.testproject.eu/sparql">SPARQL endpoint</a> of <a target="_blank" href="http://location.testproject.eu/">ISA Core Location Pilot</a> [<a target="_blank" href="http://location.testproject.eu/sparql?default-graph-uri=&query=PREFIX+locn%3A++%3Chttp%3A%2F%2Fwww.w3.org%2Fns%2Flocn%23%3E%0D%0APREFIX+vcard%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F2006%2Fvcard%2Fns%23%3E%0D%0A%0D%0ACONSTRUCT+%7B%0D%0A++%3FLocation+a+vcard%3ALocation+%3B%0D%0A++++vcard%3Afn+%3FgeographicName%0D%0A%7D+WHERE+%7B%0D%0A++%3FLocation+locn%3AgeographicName+%3FgeographicName%0D%0A%7D+LIMIT+100&format=application%2Frdf%2Bxml&timeout=0&debug=on">RDF/XML</a>] [<a target="_blank" href="http://location.testproject.eu/sparql?default-graph-uri=&query=PREFIX+locn%3A++%3Chttp%3A%2F%2Fwww.w3.org%2Fns%2Flocn%23%3E%0D%0APREFIX+vcard%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F2006%2Fvcard%2Fns%23%3E%0D%0A%0D%0ACONSTRUCT+%7B%0D%0A++%3FLocation+a+vcard%3ALocation+%3B%0D%0A++++vcard%3Afn+%3FgeographicName%0D%0A%7D+WHERE+%7B%0D%0A++%3FLocation+locn%3AgeographicName+%3FgeographicName%0D%0A%7D+LIMIT+100&format=text%2Fturtle&timeout=0&debug=on">Turtle</a>] [<a target="_blank" href="http://location.testproject.eu/sparql?default-graph-uri=&query=PREFIX+locn%3A++%3Chttp%3A%2F%2Fwww.w3.org%2Fns%2Flocn%23%3E%0D%0APREFIX+vcard%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F2006%2Fvcard%2Fns%23%3E%0D%0A%0D%0ACONSTRUCT+%7B%0D%0A++%3FLocation+a+vcard%3ALocation+%3B%0D%0A++++vcard%3Afn+%3FgeographicName%0D%0A%7D+WHERE+%7B%0D%0A++%3FLocation+locn%3AgeographicName+%3FgeographicName%0D%0A%7D+LIMIT+100&format=application%2Fld%2Bjson&timeout=0&debug=on">JSON-LD</a>]</p>

    PREFIX locn:  <http://www.w3.org/ns/locn#>
    PREFIX vcard: <http://www.w3.org/2006/vcard/ns#>

    CONSTRUCT {
      ?Location a vcard:Location ;
        vcard:fn ?geographicName
    } WHERE {
      ?Location locn:geographicName ?geographicName
    }

</section>
<section>
<h4>Mapping rules for <a target="_blank" title="http://www.w3.org/ns/locn#geometry" href="http://www.w3.org/ns/locn#locn:geometry"><code>locn:geometry</code></a></h4>
<p><strong>NB</strong>: This mapping does not addresses the geometry encoding issues mentioned in the mapping summary in relation to the mapping property <code>locn:geometry</code>.</p>
<p>Test it on the <a target="_blank" href="http://location.testproject.eu/sparql">SPARQL endpoint</a> of <a target="_blank" href="http://location.testproject.eu/">ISA Core Location Pilot</a> [<a target="_blank" href="http://location.testproject.eu/sparql?default-graph-uri=&query=PREFIX+locn%3A++%3Chttp%3A%2F%2Fwww.w3.org%2Fns%2Flocn%23%3E%0D%0APREFIX+vcard%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F2006%2Fvcard%2Fns%23%3E%0D%0A%0D%0ACONSTRUCT+%7B%0D%0A++%3FResource+vcard%3AhasGeo+%3Fgeometry%0D%0A%7D+WHERE+%7B%0D%0A++%3FResource+locn%3Ageometry+%3Fgeometry%0D%0A%7D+LIMIT+100&format=application%2Frdf%2Bxml&timeout=0&debug=on">RDF/XML</a>] [<a target="_blank" href="http://location.testproject.eu/sparql?default-graph-uri=&query=PREFIX+locn%3A++%3Chttp%3A%2F%2Fwww.w3.org%2Fns%2Flocn%23%3E%0D%0APREFIX+vcard%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F2006%2Fvcard%2Fns%23%3E%0D%0A%0D%0ACONSTRUCT+%7B%0D%0A++%3FResource+vcard%3AhasGeo+%3Fgeometry%0D%0A%7D+WHERE+%7B%0D%0A++%3FResource+locn%3Ageometry+%3Fgeometry%0D%0A%7D+LIMIT+100&format=text%2Fturtle&timeout=0&debug=on">Turtle</a>] [<a target="_blank" href="http://location.testproject.eu/sparql?default-graph-uri=&query=PREFIX+locn%3A++%3Chttp%3A%2F%2Fwww.w3.org%2Fns%2Flocn%23%3E%0D%0APREFIX+vcard%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F2006%2Fvcard%2Fns%23%3E%0D%0A%0D%0ACONSTRUCT+%7B%0D%0A++%3FResource+vcard%3AhasGeo+%3Fgeometry%0D%0A%7D+WHERE+%7B%0D%0A++%3FResource+locn%3Ageometry+%3Fgeometry%0D%0A%7D+LIMIT+100&format=application%2Fld%2Bjson&timeout=0&debug=on">JSON-LD</a>]</p>

    PREFIX locn:  <http://www.w3.org/ns/locn#>
    PREFIX vcard: <http://www.w3.org/2006/vcard/ns#>

    CONSTRUCT {
      ?Resource vcard:hasGeo ?geometry
    } WHERE {
      ?Resource locn:geometry ?geometry
    }

</section>
<section>
<h4>Mapping rules for <a target="_blank" title="http://www.w3.org/ns/locn#Geometry" href="http://www.w3.org/ns/locn#locn:Geometry"><code>locn:Geometry</code></a></h4>
<p>Because of the geometry encoding issues reported in the mapping summary about the mapping property <code>locn:geometry</code>, the mapping of class <code>locn:Geometry</code> requires syntax processing that is not addressed in the current version of this document.</p>
<p>For this reason, no mapping rule is defined here for class <code>locn:Geometry</code>.</p>
</section>
<section>
<h4>Mapping rules for <a target="_blank" title="http://www.w3.org/ns/locn#Address" href="http://www.w3.org/ns/locn#locn:Address"><code>locn:Address</code></a></h4>
<p>Test it on the <a target="_blank" href="http://location.testproject.eu/sparql">SPARQL endpoint</a> of <a target="_blank" href="http://location.testproject.eu/">ISA Core Location Pilot</a> [<a target="_blank" href="http://location.testproject.eu/sparql?default-graph-uri=&query=PREFIX+locn%3A++%3Chttp%3A%2F%2Fwww.w3.org%2Fns%2Flocn%23%3E%0D%0APREFIX+vcard%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F2006%2Fvcard%2Fns%23%3E%0D%0A%0D%0ACONSTRUCT+%7B%0D%0A++%3FResource+vcard%3AhasAddress+%3FAddress+.%0D%0A++%3FAddress+a+vcard%3AAddress+%3B%0D%0A++++vcard%3Afn+%3FfullAddress+%3B%0D%0A++++vcard%3Astreet-address+%3Fstreet_name_and_nr+%3B%0D%0A++++vcard%3Astreet-address+%3Fstreet_name+%3B%0D%0A++++vcard%3Alocality+%3FpostName+%3B%0D%0A++++vcard%3Aregion+%3FadminUnitL2+%3B%0D%0A++++vcard%3Acountry-name+%3FadminUnitL1+%3B%0D%0A++++vcard%3Apostal-code+%3FpostCode+%3B%0D%0A++++vcard%3AhasUID+%3FaddressId%0D%0A%7D+WHERE+%7B%0D%0A++OPTIONAL+%7B+%3FResource+locn%3Aaddress+%3FAddress+.+%7D%0D%0A++OPTIONAL+%7B+%3FAddress+locn%3AfullAddress+%3FfullAddress+.+%7D%0D%0A%23++OPTIONAL+%7B+%3FAddress+locn%3ApoBox+%3FpoBox+.+%7D%0D%0A++OPTIONAL+%7B+%3FAddress+locn%3Athoroughfare+%3Fthoroughfare+.+%7D%0D%0A++OPTIONAL+%7B+%3FAddress+locn%3AlocatorDesignator+%3FlocatorDesignator+.+%7D%0D%0A++OPTIONAL+%7B+%3FAddress+locn%3Athoroughfare+%3Fthoroughfare+%3B%0D%0A++++locn%3AlocatorDesignator+%3FlocatorDesignator%0D%0A++++BIND%28CONCAT%28%3Fthoroughfare%2C+%27%2C+%27%2C+%3FlocatorDesignator%29+AS+%3Fstreet_name_and_nr%29+.+%7D%0D%0A++OPTIONAL+%7B+%3FAddress+locn%3Athoroughfare+%3Fstreet_name%0D%0A++++FILTER+NOT+EXISTS+%7B+%3FAddress+locn%3AlocatorDesignator+%3FlocatorDesignator+%7D+.+%7D%0D%0A%23++OPTIONAL+%7B+%3FAddress+locn%3AlocatorName+%3FlocatorName+.+%7D%0D%0A%23++OPTIONAL+%7B+%3FAddress+locn%3AaddressArea+%3FaddressArea+.+%7D%0D%0A++OPTIONAL+%7B+%3FAddress+locn%3ApostName+%3FpostName+.+%7D%0D%0A++OPTIONAL+%7B+%3FAddress+locn%3AadminUnitL2+%3FadminUnitL2+.+%7D%0D%0A++OPTIONAL+%7B+%3FAddress+locn%3AadminUnitL1+%3FadminUnitL1+.+%7D%0D%0A++OPTIONAL+%7B+%3FAddress+locn%3ApostCode+%3FpostCode+.+%7D%0D%0A++OPTIONAL+%7B+%3FAddress+locn%3AaddressId+%3FaddressId+.+%7D%0D%0A%7D+LIMIT+100&format=application%2Frdf%2Bxml&timeout=0&debug=on">RDF/XML</a>] [<a target="_blank" href="http://location.testproject.eu/sparql?default-graph-uri=&query=PREFIX+locn%3A++%3Chttp%3A%2F%2Fwww.w3.org%2Fns%2Flocn%23%3E%0D%0APREFIX+vcard%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F2006%2Fvcard%2Fns%23%3E%0D%0A%0D%0ACONSTRUCT+%7B%0D%0A++%3FResource+vcard%3AhasAddress+%3FAddress+.%0D%0A++%3FAddress+a+vcard%3AAddress+%3B%0D%0A++++vcard%3Afn+%3FfullAddress+%3B%0D%0A++++vcard%3Astreet-address+%3Fstreet_name_and_nr+%3B%0D%0A++++vcard%3Astreet-address+%3Fstreet_name+%3B%0D%0A++++vcard%3Alocality+%3FpostName+%3B%0D%0A++++vcard%3Aregion+%3FadminUnitL2+%3B%0D%0A++++vcard%3Acountry-name+%3FadminUnitL1+%3B%0D%0A++++vcard%3Apostal-code+%3FpostCode+%3B%0D%0A++++vcard%3AhasUID+%3FaddressId%0D%0A%7D+WHERE+%7B%0D%0A++OPTIONAL+%7B+%3FResource+locn%3Aaddress+%3FAddress+.+%7D%0D%0A++OPTIONAL+%7B+%3FAddress+locn%3AfullAddress+%3FfullAddress+.+%7D%0D%0A%23++OPTIONAL+%7B+%3FAddress+locn%3ApoBox+%3FpoBox+.+%7D%0D%0A++OPTIONAL+%7B+%3FAddress+locn%3Athoroughfare+%3Fthoroughfare+.+%7D%0D%0A++OPTIONAL+%7B+%3FAddress+locn%3AlocatorDesignator+%3FlocatorDesignator+.+%7D%0D%0A++OPTIONAL+%7B+%3FAddress+locn%3Athoroughfare+%3Fthoroughfare+%3B%0D%0A++++locn%3AlocatorDesignator+%3FlocatorDesignator%0D%0A++++BIND%28CONCAT%28%3Fthoroughfare%2C+%27%2C+%27%2C+%3FlocatorDesignator%29+AS+%3Fstreet_name_and_nr%29+.+%7D%0D%0A++OPTIONAL+%7B+%3FAddress+locn%3Athoroughfare+%3Fstreet_name%0D%0A++++FILTER+NOT+EXISTS+%7B+%3FAddress+locn%3AlocatorDesignator+%3FlocatorDesignator+%7D+.+%7D%0D%0A%23++OPTIONAL+%7B+%3FAddress+locn%3AlocatorName+%3FlocatorName+.+%7D%0D%0A%23++OPTIONAL+%7B+%3FAddress+locn%3AaddressArea+%3FaddressArea+.+%7D%0D%0A++OPTIONAL+%7B+%3FAddress+locn%3ApostName+%3FpostName+.+%7D%0D%0A++OPTIONAL+%7B+%3FAddress+locn%3AadminUnitL2+%3FadminUnitL2+.+%7D%0D%0A++OPTIONAL+%7B+%3FAddress+locn%3AadminUnitL1+%3FadminUnitL1+.+%7D%0D%0A++OPTIONAL+%7B+%3FAddress+locn%3ApostCode+%3FpostCode+.+%7D%0D%0A++OPTIONAL+%7B+%3FAddress+locn%3AaddressId+%3FaddressId+.+%7D%0D%0A%7D+LIMIT+100&format=text%2Fturtle&timeout=0&debug=on">Turtle</a>] [<a target="_blank" href="http://location.testproject.eu/sparql?default-graph-uri=&query=PREFIX+locn%3A++%3Chttp%3A%2F%2Fwww.w3.org%2Fns%2Flocn%23%3E%0D%0APREFIX+vcard%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F2006%2Fvcard%2Fns%23%3E%0D%0A%0D%0ACONSTRUCT+%7B%0D%0A++%3FResource+vcard%3AhasAddress+%3FAddress+.%0D%0A++%3FAddress+a+vcard%3AAddress+%3B%0D%0A++++vcard%3Afn+%3FfullAddress+%3B%0D%0A++++vcard%3Astreet-address+%3Fstreet_name_and_nr+%3B%0D%0A++++vcard%3Astreet-address+%3Fstreet_name+%3B%0D%0A++++vcard%3Alocality+%3FpostName+%3B%0D%0A++++vcard%3Aregion+%3FadminUnitL2+%3B%0D%0A++++vcard%3Acountry-name+%3FadminUnitL1+%3B%0D%0A++++vcard%3Apostal-code+%3FpostCode+%3B%0D%0A++++vcard%3AhasUID+%3FaddressId%0D%0A%7D+WHERE+%7B%0D%0A++OPTIONAL+%7B+%3FResource+locn%3Aaddress+%3FAddress+.+%7D%0D%0A++OPTIONAL+%7B+%3FAddress+locn%3AfullAddress+%3FfullAddress+.+%7D%0D%0A%23++OPTIONAL+%7B+%3FAddress+locn%3ApoBox+%3FpoBox+.+%7D%0D%0A++OPTIONAL+%7B+%3FAddress+locn%3Athoroughfare+%3Fthoroughfare+.+%7D%0D%0A++OPTIONAL+%7B+%3FAddress+locn%3AlocatorDesignator+%3FlocatorDesignator+.+%7D%0D%0A++OPTIONAL+%7B+%3FAddress+locn%3Athoroughfare+%3Fthoroughfare+%3B%0D%0A++++locn%3AlocatorDesignator+%3FlocatorDesignator%0D%0A++++BIND%28CONCAT%28%3Fthoroughfare%2C+%27%2C+%27%2C+%3FlocatorDesignator%29+AS+%3Fstreet_name_and_nr%29+.+%7D%0D%0A++OPTIONAL+%7B+%3FAddress+locn%3Athoroughfare+%3Fstreet_name%0D%0A++++FILTER+NOT+EXISTS+%7B+%3FAddress+locn%3AlocatorDesignator+%3FlocatorDesignator+%7D+.+%7D%0D%0A%23++OPTIONAL+%7B+%3FAddress+locn%3AlocatorName+%3FlocatorName+.+%7D%0D%0A%23++OPTIONAL+%7B+%3FAddress+locn%3AaddressArea+%3FaddressArea+.+%7D%0D%0A++OPTIONAL+%7B+%3FAddress+locn%3ApostName+%3FpostName+.+%7D%0D%0A++OPTIONAL+%7B+%3FAddress+locn%3AadminUnitL2+%3FadminUnitL2+.+%7D%0D%0A++OPTIONAL+%7B+%3FAddress+locn%3AadminUnitL1+%3FadminUnitL1+.+%7D%0D%0A++OPTIONAL+%7B+%3FAddress+locn%3ApostCode+%3FpostCode+.+%7D%0D%0A++OPTIONAL+%7B+%3FAddress+locn%3AaddressId+%3FaddressId+.+%7D%0D%0A%7D+LIMIT+100&format=application%2Fld%2Bjson&timeout=0&debug=on">JSON-LD</a>]</p>

    PREFIX locn:  <http://www.w3.org/ns/locn#>
    PREFIX vcard: <http://www.w3.org/2006/vcard/ns#>

    CONSTRUCT {
      ?Resource vcard:hasAddress ?Address .
      ?Address a vcard:Address ;
        vcard:fn ?fullAddress ;
        vcard:street-address ?street_name_and_nr ;
        vcard:street-address ?street_name ;
        vcard:locality ?postName ;
        vcard:region ?adminUnitL2 ;
        vcard:country-name ?adminUnitL1 ;
        vcard:postal-code ?postCode ;
        vcard:hasUID ?addressId
    } WHERE {
      OPTIONAL { ?Resource locn:address ?Address . }
      OPTIONAL { ?Address locn:fullAddress ?fullAddress . }
    #  OPTIONAL { ?Address locn:poBox ?poBox . }
      OPTIONAL { ?Address locn:thoroughfare ?thoroughfare . }
      OPTIONAL { ?Address locn:locatorDesignator ?locatorDesignator . }
      OPTIONAL { ?Address locn:thoroughfare ?thoroughfare ;
        locn:locatorDesignator ?locatorDesignator
        BIND(CONCAT(?thoroughfare, ', ', ?locatorDesignator) AS ?street_name_and_nr) . }
      OPTIONAL { ?Address locn:thoroughfare ?street_name
        FILTER NOT EXISTS { ?Address locn:locatorDesignator ?locatorDesignator } . }
    #  OPTIONAL { ?Address locn:locatorName ?locatorName . }
    #  OPTIONAL { ?Address locn:addressArea ?addressArea . }
      OPTIONAL { ?Address locn:postName ?postName . }
      OPTIONAL { ?Address locn:adminUnitL2 ?adminUnitL2 . }
      OPTIONAL { ?Address locn:adminUnitL1 ?adminUnitL1 . }
      OPTIONAL { ?Address locn:postCode ?postCode . }
      OPTIONAL { ?Address locn:addressId ?addressId . }
    }

</section>
</section>
<section id="formal-definition-sparql-locn-2-schema.org">
<h3><a name="formal-definition-sparql-locn-2-schema.org">LOCN to Schema.org mapping</a></h3>
<section>
<h4>Mapping rules for <a target="_blank" title="http://www.w3.org/ns/locn#geographicName" href="http://www.w3.org/ns/locn#locn:geographicName"><code>locn:geographicName</code></a></h4>
<p>Test it on the <a target="_blank" href="http://location.testproject.eu/sparql">SPARQL endpoint</a> of <a target="_blank" href="http://location.testproject.eu/">ISA Core Location Pilot</a> [<a target="_blank" href="http://location.testproject.eu/sparql?default-graph-uri=&query=PREFIX+locn%3A+++%3Chttp%3A%2F%2Fwww.w3.org%2Fns%2Flocn%23%3E%0D%0APREFIX+schema%3A+%3Chttp%3A%2F%2Fschema.org%2F%3E%0D%0A%0D%0ACONSTRUCT+%7B%0D%0A%3FLocation+a+schema%3APlace+%3B%0D%0A++schema%3Aname+%3FgeographicName%0D%0A%7D+WHERE+%7B%0D%0A%3FLocation+locn%3AgeographicName+%3FgeographicName%0D%0A%7D+LIMIT+100&format=application%2Frdf%2Bxml&timeout=0&debug=on">RDF/XML</a>] [<a target="_blank" href="http://location.testproject.eu/sparql?default-graph-uri=&query=PREFIX+locn%3A+++%3Chttp%3A%2F%2Fwww.w3.org%2Fns%2Flocn%23%3E%0D%0APREFIX+schema%3A+%3Chttp%3A%2F%2Fschema.org%2F%3E%0D%0A%0D%0ACONSTRUCT+%7B%0D%0A%3FLocation+a+schema%3APlace+%3B%0D%0A++schema%3Aname+%3FgeographicName%0D%0A%7D+WHERE+%7B%0D%0A%3FLocation+locn%3AgeographicName+%3FgeographicName%0D%0A%7D+LIMIT+100&format=text%2Fturtle&timeout=0&debug=on">Turtle</a>] [<a target="_blank" href="http://location.testproject.eu/sparql?default-graph-uri=&query=PREFIX+locn%3A+++%3Chttp%3A%2F%2Fwww.w3.org%2Fns%2Flocn%23%3E%0D%0APREFIX+schema%3A+%3Chttp%3A%2F%2Fschema.org%2F%3E%0D%0A%0D%0ACONSTRUCT+%7B%0D%0A%3FLocation+a+schema%3APlace+%3B%0D%0A++schema%3Aname+%3FgeographicName%0D%0A%7D+WHERE+%7B%0D%0A%3FLocation+locn%3AgeographicName+%3FgeographicName%0D%0A%7D+LIMIT+100&format=application%2Fld%2Bjson&timeout=0&debug=on">JSON-LD</a>]</p>

    PREFIX locn:   <http://www.w3.org/ns/locn#>
    PREFIX schema: <http://schema.org/>

    CONSTRUCT {
      ?Location a schema:Place ;
        schema:name ?geographicName
    } WHERE {
      ?Location locn:geographicName ?geographicName
    }

</section>
<section>
<h4>Mappings rules for <a target="_blank" title="http://www.w3.org/ns/locn#geometry" href="http://www.w3.org/ns/locn#locn:geometry"><code>locn:geometry</code></a></h4>
<p>Test it on the <a target="_blank" href="http://location.testproject.eu/sparql">SPARQL endpoint</a> of <a target="_blank" href="http://location.testproject.eu/">ISA Core Location Pilot</a> [<a target="_blank" href="http://location.testproject.eu/sparql?default-graph-uri=&query=PREFIX+locn%3A+++%3Chttp%3A%2F%2Fwww.w3.org%2Fns%2Flocn%23%3E%0D%0APREFIX+schema%3A+%3Chttp%3A%2F%2Fschema.org%2F%3E%0D%0A%0D%0ACONSTRUCT+%7B%0D%0A%3FResource+schema%3Ageo+%3Fgeometry%0D%0A%7D+WHERE+%7B%0D%0A%3FResource+locn%3Ageometry+%3Fgeometry%0D%0A%7D+LIMIT+100&format=application%2Frdf%2Bxml&timeout=0&debug=on">RDF/XML</a>] [<a target="_blank" href="http://location.testproject.eu/sparql?default-graph-uri=&query=PREFIX+locn%3A+++%3Chttp%3A%2F%2Fwww.w3.org%2Fns%2Flocn%23%3E%0D%0APREFIX+schema%3A+%3Chttp%3A%2F%2Fschema.org%2F%3E%0D%0A%0D%0ACONSTRUCT+%7B%0D%0A%3FResource+schema%3Ageo+%3Fgeometry%0D%0A%7D+WHERE+%7B%0D%0A%3FResource+locn%3Ageometry+%3Fgeometry%0D%0A%7D+LIMIT+100&format=text%2Fturtle&timeout=0&debug=on">Turtle</a>] [<a target="_blank" href="http://location.testproject.eu/sparql?default-graph-uri=&query=PREFIX+locn%3A+++%3Chttp%3A%2F%2Fwww.w3.org%2Fns%2Flocn%23%3E%0D%0APREFIX+schema%3A+%3Chttp%3A%2F%2Fschema.org%2F%3E%0D%0A%0D%0ACONSTRUCT+%7B%0D%0A%3FResource+schema%3Ageo+%3Fgeometry%0D%0A%7D+WHERE+%7B%0D%0A%3FResource+locn%3Ageometry+%3Fgeometry%0D%0A%7D+LIMIT+100&format=application%2Fld%2Bjson&timeout=0&debug=on">JSON-LD</a>]</p>

    PREFIX locn:   <http://www.w3.org/ns/locn#>
    PREFIX schema: <http://schema.org/>

    CONSTRUCT {
      ?Resource schema:geo ?geometry
    } WHERE {
      ?Resource locn:geometry ?geometry
    }

</section>
<section>
<h4>Mapping rules for <a target="_blank" title="http://www.w3.org/ns/locn#Address" href="http://www.w3.org/ns/locn#locn:Address"><code>locn:Address</code></a></h4>
<p>Test it on the <a target="_blank" href="http://location.testproject.eu/sparql">SPARQL endpoint</a> of <a target="_blank" href="http://location.testproject.eu/">ISA Core Location Pilot</a> [<a target="_blank" href="http://location.testproject.eu/sparql?default-graph-uri=&query=PREFIX+locn%3A+++%3Chttp%3A%2F%2Fwww.w3.org%2Fns%2Flocn%23%3E%0D%0APREFIX+schema%3A+%3Chttp%3A%2F%2Fschema.org%2F%3E%0D%0A%0D%0ACONSTRUCT+%7B%0D%0A%3FResource+schema%3Aaddress+%3FAddress+.%0D%0A%3FAddress+a+schema%3APostalAddress+%3B%0D%0A++schema%3Aname+%3FfullAddress+%3B%0D%0A++schema%3AstreetAddress+%3Fstreet_name_and_nr+%3B%0D%0A++schema%3AstreetAddress+%3Fstreet_name+%3B%0D%0A++schema%3AaddressLocality+%3FpostName+%3B%0D%0A++schema%3AaddressRegion+%3FadminUnitL2+%3B%0D%0A++schema%3AaddressCountry+%3FadminUnitL1+%3B%0D%0A++schema%3ApostalCode+%3FpostCode%0D%0A%7D+WHERE+%7B%0D%0AOPTIONAL+%7B+%3FResource+locn%3Aaddress+%3FAddress+.+%7D%0D%0AOPTIONAL+%7B+%3FAddress+locn%3AfullAddress+%3FfullAddress+.+%7D%0D%0AOPTIONAL+%7B+%3FAddress+locn%3ApoBox+%3FpoBox+.+%7D%0D%0AOPTIONAL+%7B+%3FAddress+locn%3Athoroughfare+%3Fthoroughfare+.+%7D%0D%0AOPTIONAL+%7B+%3FAddress+locn%3AlocatorDesignator+%3FlocatorDesignator+.+%7D%0D%0AOPTIONAL+%7B+%3FAddress+locn%3Athoroughfare+%3Fthoroughfare+%3B%0D%0A++locn%3AlocatorDesignator+%3FlocatorDesignator%0D%0A++BIND%28CONCAT%28%3Fthoroughfare%2C+%27%2C+%27%2C+%3FlocatorDesignator%29+AS+%3Fstreet_name_and_nr%29+.+%7D%0D%0AOPTIONAL+%7B+%3FAddress+locn%3Athoroughfare+%3Fstreet_name%0D%0A++FILTER+NOT+EXISTS+%7B+%3FAddress+locn%3AlocatorDesignator+%3FlocatorDesignator+%7D+.+%7D%0D%0A%23++OPTIONAL+%7B+%3FAddress+locn%3AlocatorName+%3FlocatorName+.+%7D%0D%0A%23++OPTIONAL+%7B+%3FAddress+locn%3AaddressArea+%3FaddressArea+.+%7D%0D%0AOPTIONAL+%7B+%3FAddress+locn%3ApostName+%3FpostName+.+%7D%0D%0AOPTIONAL+%7B+%3FAddress+locn%3AadminUnitL2+%3FadminUnitL2+.+%7D%0D%0AOPTIONAL+%7B+%3FAddress+locn%3AadminUnitL1+%3FadminUnitL1+.+%7D%0D%0AOPTIONAL+%7B+%3FAddress+locn%3ApostCode+%3FpostCode+.+%7D%0D%0A%23++OPTIONAL+%7B+%3FAddress+locn%3AaddressId+%3FaddressId+.+%7D%0D%0A%7D+LIMIT+100&format=application%2Frdf%2Bxml&timeout=0&debug=on">RDF/XML</a>] [<a target="_blank" href="http://location.testproject.eu/sparql?default-graph-uri=&query=PREFIX+locn%3A+++%3Chttp%3A%2F%2Fwww.w3.org%2Fns%2Flocn%23%3E%0D%0APREFIX+schema%3A+%3Chttp%3A%2F%2Fschema.org%2F%3E%0D%0A%0D%0ACONSTRUCT+%7B%0D%0A%3FResource+schema%3Aaddress+%3FAddress+.%0D%0A%3FAddress+a+schema%3APostalAddress+%3B%0D%0A++schema%3Aname+%3FfullAddress+%3B%0D%0A++schema%3AstreetAddress+%3Fstreet_name_and_nr+%3B%0D%0A++schema%3AstreetAddress+%3Fstreet_name+%3B%0D%0A++schema%3AaddressLocality+%3FpostName+%3B%0D%0A++schema%3AaddressRegion+%3FadminUnitL2+%3B%0D%0A++schema%3AaddressCountry+%3FadminUnitL1+%3B%0D%0A++schema%3ApostalCode+%3FpostCode%0D%0A%7D+WHERE+%7B%0D%0AOPTIONAL+%7B+%3FResource+locn%3Aaddress+%3FAddress+.+%7D%0D%0AOPTIONAL+%7B+%3FAddress+locn%3AfullAddress+%3FfullAddress+.+%7D%0D%0AOPTIONAL+%7B+%3FAddress+locn%3ApoBox+%3FpoBox+.+%7D%0D%0AOPTIONAL+%7B+%3FAddress+locn%3Athoroughfare+%3Fthoroughfare+.+%7D%0D%0AOPTIONAL+%7B+%3FAddress+locn%3AlocatorDesignator+%3FlocatorDesignator+.+%7D%0D%0AOPTIONAL+%7B+%3FAddress+locn%3Athoroughfare+%3Fthoroughfare+%3B%0D%0A++locn%3AlocatorDesignator+%3FlocatorDesignator%0D%0A++BIND%28CONCAT%28%3Fthoroughfare%2C+%27%2C+%27%2C+%3FlocatorDesignator%29+AS+%3Fstreet_name_and_nr%29+.+%7D%0D%0AOPTIONAL+%7B+%3FAddress+locn%3Athoroughfare+%3Fstreet_name%0D%0A++FILTER+NOT+EXISTS+%7B+%3FAddress+locn%3AlocatorDesignator+%3FlocatorDesignator+%7D+.+%7D%0D%0A%23++OPTIONAL+%7B+%3FAddress+locn%3AlocatorName+%3FlocatorName+.+%7D%0D%0A%23++OPTIONAL+%7B+%3FAddress+locn%3AaddressArea+%3FaddressArea+.+%7D%0D%0AOPTIONAL+%7B+%3FAddress+locn%3ApostName+%3FpostName+.+%7D%0D%0AOPTIONAL+%7B+%3FAddress+locn%3AadminUnitL2+%3FadminUnitL2+.+%7D%0D%0AOPTIONAL+%7B+%3FAddress+locn%3AadminUnitL1+%3FadminUnitL1+.+%7D%0D%0AOPTIONAL+%7B+%3FAddress+locn%3ApostCode+%3FpostCode+.+%7D%0D%0A%23++OPTIONAL+%7B+%3FAddress+locn%3AaddressId+%3FaddressId+.+%7D%0D%0A%7D+LIMIT+100&format=text%2Fturtle&timeout=0&debug=on">Turtle</a>] [<a target="_blank" href="http://location.testproject.eu/sparql?default-graph-uri=&query=PREFIX+locn%3A+++%3Chttp%3A%2F%2Fwww.w3.org%2Fns%2Flocn%23%3E%0D%0APREFIX+schema%3A+%3Chttp%3A%2F%2Fschema.org%2F%3E%0D%0A%0D%0ACONSTRUCT+%7B%0D%0A%3FResource+schema%3Aaddress+%3FAddress+.%0D%0A%3FAddress+a+schema%3APostalAddress+%3B%0D%0A++schema%3Aname+%3FfullAddress+%3B%0D%0A++schema%3AstreetAddress+%3Fstreet_name_and_nr+%3B%0D%0A++schema%3AstreetAddress+%3Fstreet_name+%3B%0D%0A++schema%3AaddressLocality+%3FpostName+%3B%0D%0A++schema%3AaddressRegion+%3FadminUnitL2+%3B%0D%0A++schema%3AaddressCountry+%3FadminUnitL1+%3B%0D%0A++schema%3ApostalCode+%3FpostCode%0D%0A%7D+WHERE+%7B%0D%0AOPTIONAL+%7B+%3FResource+locn%3Aaddress+%3FAddress+.+%7D%0D%0AOPTIONAL+%7B+%3FAddress+locn%3AfullAddress+%3FfullAddress+.+%7D%0D%0AOPTIONAL+%7B+%3FAddress+locn%3ApoBox+%3FpoBox+.+%7D%0D%0AOPTIONAL+%7B+%3FAddress+locn%3Athoroughfare+%3Fthoroughfare+.+%7D%0D%0AOPTIONAL+%7B+%3FAddress+locn%3AlocatorDesignator+%3FlocatorDesignator+.+%7D%0D%0AOPTIONAL+%7B+%3FAddress+locn%3Athoroughfare+%3Fthoroughfare+%3B%0D%0A++locn%3AlocatorDesignator+%3FlocatorDesignator%0D%0A++BIND%28CONCAT%28%3Fthoroughfare%2C+%27%2C+%27%2C+%3FlocatorDesignator%29+AS+%3Fstreet_name_and_nr%29+.+%7D%0D%0AOPTIONAL+%7B+%3FAddress+locn%3Athoroughfare+%3Fstreet_name%0D%0A++FILTER+NOT+EXISTS+%7B+%3FAddress+locn%3AlocatorDesignator+%3FlocatorDesignator+%7D+.+%7D%0D%0A%23++OPTIONAL+%7B+%3FAddress+locn%3AlocatorName+%3FlocatorName+.+%7D%0D%0A%23++OPTIONAL+%7B+%3FAddress+locn%3AaddressArea+%3FaddressArea+.+%7D%0D%0AOPTIONAL+%7B+%3FAddress+locn%3ApostName+%3FpostName+.+%7D%0D%0AOPTIONAL+%7B+%3FAddress+locn%3AadminUnitL2+%3FadminUnitL2+.+%7D%0D%0AOPTIONAL+%7B+%3FAddress+locn%3AadminUnitL1+%3FadminUnitL1+.+%7D%0D%0AOPTIONAL+%7B+%3FAddress+locn%3ApostCode+%3FpostCode+.+%7D%0D%0A%23++OPTIONAL+%7B+%3FAddress+locn%3AaddressId+%3FaddressId+.+%7D%0D%0A%7D+LIMIT+100&format=application%2Fld%2Bjson&timeout=0&debug=on">JSON-LD</a>]</p>

    PREFIX locn:   <http://www.w3.org/ns/locn#>
    PREFIX schema: <http://schema.org/>

    CONSTRUCT {
      ?Resource schema:address ?Address .
      ?Address a schema:PostalAddress ;
        schema:name ?fullAddress ;
        schema:streetAddress ?street_name_and_nr ;
        schema:streetAddress ?street_name ;
        schema:addressLocality ?postName ;
        schema:addressRegion ?adminUnitL2 ;
        schema:addressCountry ?adminUnitL1 ;
        schema:postalCode ?postCode
    } WHERE {
      OPTIONAL { ?Resource locn:address ?Address . }
      OPTIONAL { ?Address locn:fullAddress ?fullAddress . }
      OPTIONAL { ?Address locn:poBox ?poBox . }
      OPTIONAL { ?Address locn:thoroughfare ?thoroughfare . }
      OPTIONAL { ?Address locn:locatorDesignator ?locatorDesignator . }
      OPTIONAL { ?Address locn:thoroughfare ?thoroughfare ;
        locn:locatorDesignator ?locatorDesignator
        BIND(CONCAT(?thoroughfare, ', ', ?locatorDesignator) AS ?street_name_and_nr) . }
      OPTIONAL { ?Address locn:thoroughfare ?street_name
        FILTER NOT EXISTS { ?Address locn:locatorDesignator ?locatorDesignator } . }
    #  OPTIONAL { ?Address locn:locatorName ?locatorName . }
    #  OPTIONAL { ?Address locn:addressArea ?addressArea . }
      OPTIONAL { ?Address locn:postName ?postName . }
      OPTIONAL { ?Address locn:adminUnitL2 ?adminUnitL2 . }
      OPTIONAL { ?Address locn:adminUnitL1 ?adminUnitL1 . }
      OPTIONAL { ?Address locn:postCode ?postCode . }
    #  OPTIONAL { ?Address locn:addressId ?addressId . }
    }

</section>
</section>
</section>
</article>  

