<div style="text-align: center; color: #8000FF">
if/then/else
</div>

<span style="font-size: 28px"><em style="text-align: left !important;">SHACL allows to define a (sort of) grammar <br/> and expansion rules for a defined vocabulary.</em></span>

+++


<pre style="font-size: 0.55em; line-height: 1.3;">
<code class="turtle" data-line-numbers>ex:Shape a sh:NodeShape ;
	sh:targetNode &lt;urn:target&gt; ;
	:if [
		sh:property [
			sh:path &lt;urn:x&gt; ;
			sh:minCount 1 ;
			sh:maxCount 1
			]
		] ;
	:then [
		sh:property [
			sh:path &lt;urn:y&gt; ;
			sh:minCount 1 ;
			sh:maxCount 1
		]
	] ;
	:else [
		sh:property [
			sh:path &lt;urn:z&gt; ;
			sh:minCount 1 ;
			sh:maxCount 1
		]
	] .
</code>
</pre>

+++

<pre style="font-size: 0.55em; line-height: 1.3;">
<code class="turtle" data-line-numbers>ex:Shape a sh:NodeShape ;
	sh:targetNode &lt;urn:target&gt; ;
	sh:or (
		[
			sh:not [
				sh:property [
					sh:minCount 1 ;
					sh:maxCount 1 ;
					sh:path &lt;urn:x&gt;
				]
			]
		]
		[
			sh:property [
				sh:minCount 1 ;
				sh:maxCount 1 ;
				sh:path &lt;urn:y&gt;
			]
		]
	),
	(
		[
			sh:property [
				sh:minCount 1 ;
				sh:maxCount 1 ;
				sh:path &lt;urn:x&gt;
			]
		]
		[
			sh:property [
				sh:minCount 1 ;
				sh:maxCount 1 ;
				sh:path &lt;urn:z&gt;
			]
		]
	) .

</code>
</pre>

+++

<span style="font-size: 28px"><em style="text-align: left !important;">Passes validation</em></span>

<pre>
<code class="turtle" data-line-numbers>&lt;urn:target&gt; &lt;urn:x&gt; "literal" ;
	&lt;urn:y&gt; "other literal" .
</code>
</pre>

<pre>
<code class="turtle" data-line-numbers>&lt;urn:target&gt; &lt;urn:z&gt; "yet another literal" .
</code>
</pre>

<pre>
<code class="turtle" data-line-numbers>&lt;urn:target&gt; &lt;urn:y&gt; "other literal" ;
	&lt;urn:z&gt; "yet another literal"
</code>
</pre>

<span style="font-size: 28px"><em style="text-align: left !important;">Fails validation</em></span>

<pre>
<code class="turtle" data-line-numbers>&lt;urn:target&gt; &lt;urn:x&gt; "literal" .
</code>
</pre>

<pre>
<code class="turtle" data-line-numbers>&lt;urn:target&gt; &lt;urn:y&gt; "other literal" .
</code>
</pre>

<pre>
<code class="turtle" data-line-numbers>&lt;urn:target&gt; &lt;urn:x&gt; "literal" ;
	&lt;urn:z&gt; "yet another literal"
</code>
</pre>
