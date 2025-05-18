<div style="text-align: center; color: #8000FF">
SHACL
</div>

<span style="font-size: 28px"><em style="text-align: left !important;">Constraint Language for RDF Knowledge Graphs</em></span>


<pre>
<code class="turtle" data-line-numbers>@prefix ex: &lt;https://example.com/&gt; .
@prefix sh: &lt;http://www.w3.org/ns/shacl#&gt; .

ex:BoolShape a sh:NodeShape ;
	sh:targetClass ex:Bool ;
	sh:property [
		sh:path ex:value ;
		sh:minCount 1 ;
		sh:maxCount 1 ;
		sh:in (ex:true ex:false)
	  ] .
</code>
</pre>

+++

<span style="font-size: 28px"><em style="text-align: left !important;">Passes validation</em></span>

<pre>
<code class="turtle" data-line-numbers>@prefix ex: &lt;https://example.com/&gt; .

ex:1 a ex:Bool ;
	ex:value  ex:true.

ex:2 a ex:Bool ;
	ex:value  ex:false.
</code>
</pre>

+++

<span style="font-size: 28px"><em style="text-align: left !important;">Fails validation</em></span>

<pre>
<code class="turtle" data-line-numbers>@prefix ex: &lt;https://example.com/&gt; .

ex:3 a ex:Bool .

ex:4 a ex:Bool ;
	ex:value  ex:true, ex:false .
</code>
</pre>
