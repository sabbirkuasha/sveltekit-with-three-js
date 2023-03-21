<script>
	import { Canvas } from '@threlte/core';
	import SceneOne from '../lib/SceneOne.svelte';
</script>

<section class="p-5">
	<h2 class="mb-5">Scene One</h2>

	<div class="canvas-wrapper ring h-[500px]">
		<Canvas>
			<SceneOne />
			<!-- SceneOne -->
		</Canvas>
	</div>
</section>
