<script>
	import { Canvas } from '@threlte/core';
	import SceneOne from '../lib/SceneOne.svelte';
	import SceneTwo from '../lib/SceneTwo.svelte';
	import SceneHelmet from '../lib/SceneHelmet.svelte';
	import { Theatre } from '@threlte/theatre';

	import { getProject } from '@theatre/core';
	import projectState from '../lib/scene-two-state-blue.json';

	// This will create a project called "My Project"
	// or return it if it already exists:
	// const project = getProject('My Project', { state: projectState });

	const url = 'favicon.png';
	// console.log(url);
</script>

<section class="p-5">
	<h2 class="mb-5">Scene One</h2>

	<div class="canvas-wrapper ring h-[500px]">
		<Canvas>
			<SceneHelmet />
			<!-- SceneOne -->
		</Canvas>
	</div>
</section>
<section class="p-5">
	<h2 class="mb-5">Scene One</h2>

	<div class="canvas-wrapper ring h-[500px]">
		<Canvas>
			<SceneOne />
			<!-- SceneOne -->
		</Canvas>
	</div>
</section>
<img class="w-20 h-20" src={url} alt="" />
<section class="p-5">
	<h2 class="mb-5">Scene Two</h2>

	<div class="canvas-wrapper ring h-[700px]">
		<Canvas shadows={true}>
			<Theatre studio={false}>
				<SceneTwo />
			</Theatre>
			<!-- SceneTwo -->
		</Canvas>
	</div>
</section>
