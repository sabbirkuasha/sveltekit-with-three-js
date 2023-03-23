<script>
	import { PerspectiveCamera, DirectionalLight, AmbientLight, OrbitControls } from '@threlte/core';
	import { GLTF } from '@threlte/extras';
	import { Editable } from '@threlte/theatre';

	const url = 'free_cyberpunk_hovercar/scene.gltf';
</script>

<PerspectiveCamera fov={30} position={{ x: 0, y: 1, z: -7 }} lookAt={{ y: 0 }}>
	<OrbitControls enableDamping />
	<Editable name="PerspectiveCamera" fov position lookAt />
</PerspectiveCamera>
<DirectionalLight shadow color={'#EDBD9C'} position={{ x: -15, y: 45, z: 20 }}>
	<Editable name="Lights / Main" color intensity transform controls />
</DirectionalLight>

<GLTF
	castShadow
	receiveShadow
	{url}
	scale={1}
	position={{ x: 0, y: -0.6, z: 0 }}
	rotation={{ x: 0, y: 4, z: 0 }}
>
	<Editable name="Car" castShadow />
</GLTF>
