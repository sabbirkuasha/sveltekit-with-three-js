<script>
	import { Theatre } from '@threlte/theatre';
	import { Canvas } from '@threlte/core';
	import SceneHelmet from '../../lib/SceneHelmet.svelte';
</script>

<section class="p-5">
	<h2 class="mb-5">Helmet</h2>

	<div class="canvas-wrapper ring h-[800px]">
		<Canvas>
			<SceneHelmet />
		</Canvas>
	</div>
</section>
