<div style="text-align: center; color: #8000FF">
SPARQL
</div>

<span style="font-size: 28px"><em style="text-align: left !important;">Query Language for RDF Knowledge Graphs</em></span>


<pre>
<code class="sparql" data-line-numbers>SELECT ?s ?p ?o
WHERE {
   ?s ?p ?o .
}
</code>
</pre>


<pre>
<code class="sparql" data-line-numbers>CONSTRUCT {
	?s ?p ?o .
}
WHERE {
   ?s ?p ?o .
}
</code>
</pre>

</div>
