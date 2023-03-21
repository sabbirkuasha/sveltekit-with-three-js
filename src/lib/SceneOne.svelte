<script>
	import { PerspectiveCamera, DirectionalLight, AmbientLight, Mesh } from '@threlte/core';
	import { MeshStandardMaterial, IcosahedronGeometry } from 'three';
	import { tweened } from 'svelte/motion';

	const t = tweened(3, { duration: 2000 });
	setTimeout(() => {
		t.set(-3);
	});
</script>

<PerspectiveCamera position={{ y: 0, z: 20 }} lookAt={{ x: 0, y: 0, z: 0 }} />

<DirectionalLight />
<AmbientLight />

<Mesh
	geometry={new IcosahedronGeometry()}
	material={new MeshStandardMaterial({ color: 'seagreen' })}
	position={{ x: 0, y: 0, z: 15 }}
	rotation={{ x: 0, y: $t, z: 0 }}
/>
