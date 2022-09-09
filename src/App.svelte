<script>
	import First from './First.svelte';
	import Second from './Second.svelte';
	
	function mountFirstComponent() {
		new First({target: document.querySelector('#first-field')});
	}
	
	function mountSecondComponent() {
		new Second({target: document.querySelector('#second-field')});
	}
	
</script>

<div>
<h1>App</h1>
	<div id="second-field" />
	
	<button on:click={mountFirstComponent}>
		mount component without target
	</button>
	<button on:click={mountSecondComponent}>
		mount component with target
	</button>


<div id="instructions" style="max-width: 900px;">
	<h2>README</h2>

<span style="background-color: yellow;">Note: Issue only reproducible with prod build</span>
<p>Trying to mount first component with a target that is not present in DOM. So, this should fail to mount and throw an error (and this behaviour is correct). But when we try to mount component with a valid target, right after the first component, this second component fails to mount too.</p>

<ul>
	<li>run <code>npm run build && npm run start</code></li>
	<li>Click on 'mount component without target' button</li>
	<p>this fails with error <code>Uncaught TypeError: Cannot read properties of undefined (reading '$$')</code> </p>
	<li>Click on 'mount component with target' button</li>
	<p>
		This fails to load too with error <code>Uncaught TypeError: Cannot read properties of undefined (reading 'context')</code>
	</p>
</ul>
</div>
</div>