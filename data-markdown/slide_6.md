<div style="text-align: center; color: #8000FF">
sh:SPARQLRule
</div>

<span style="font-size: 28px"><em style="text-align: left !important;">SHACL AF rule that allows to execute a SPARQL CONSTRUCT query <br/>and materialize the constructed triples into the data graph.</em></span>

+++

<pre>
<code class="turtle" data-line-numbers>@prefix ex: &lt;https://example.com/&gt; .
@prefix sh: &lt;http://www.w3.org/ns/shacl#&gt; .

ex:Shape a sh:NodeShape ;
	sh:targetSubjectsOf ex:p ;
	sh:rule [
		a sh:SPARQLRule ;
		sh:construct '''
		prefix ex: &lt;https://example.com/&gt;

		construct {
			$this ex:q 'q literal' .
		}
		where {}
		'''
] .
</code>
</pre>

+++

<span style="font-size: 28px"><em style="text-align: left !important;">Data graph</em></span>

<pre>
<code class="turtle" data-line-numbers>@prefix ex: &lt;https://example.com/&gt; .

&lt;urn:target&gt; ex:p "p literal" .
</code>
</pre>

<span style="font-size: 28px"><em style="text-align: left !important;">Validated data graph</em></span>

<pre>
<code class="turtle" data-line-numbers>@prefix ex: &lt;https://example.com/&gt; .

&lt;urn:target&gt; ex:p "p literal" ;
	ex:q "q literal" .
</code>
</pre>
