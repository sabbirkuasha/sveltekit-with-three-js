<script>
	import { PerspectiveCamera, DirectionalLight, AmbientLight, Mesh, useFrame } from '@threlte/core';
	import { MeshStandardMaterial, IcosahedronGeometry } from 'three';
	import { tweened } from 'svelte/motion';

	// tweened take a new number and go from defined number (which is 3 in this case) to that new number
	// whithin defined duration (which is 2000 in our case)
	const t = tweened(0, { duration: 2000 });
	const t2 = tweened(1, { duration: 50 });
	// setTimeout(() => {
	// 	t.set(-3);
	// });

	let rotation = 0;
	useFrame(() => {
		rotation += 0.01;
	});
</script>

<PerspectiveCamera position={{ y: 0, z: 20 }} lookAt={{ x: 0, y: 0, z: 0 }} />

<DirectionalLight />
<AmbientLight />

<!-- when we want to interact with any 3d object we must set the properties to 'interactive' -->
<Mesh
	geometry={new IcosahedronGeometry()}
	material={new MeshStandardMaterial({ color: 'seagreen' })}
	position={{ x: $t, y: 0, z: 15 }}
	rotation={{ x: rotation, y: 0, z: rotation }}
	scale={$t2}
	interactive
	on:pointerleave={() => {
		$t2 = 1;
		// console.log('reverse pointer enter');
	}}
	on:pointerenter={() => {
		$t2 = 1.3;
		// console.log('pointer enter');
	}}
	on:click={() => {
		$t = $t > 0 ? -4 : 4;
	}}
/>
