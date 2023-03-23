<script>
	import {
		OrbitControls,
		DirectionalLight,
		Group,
		Object3DInstance,
		PerspectiveCamera,
		useFrame
	} from '@threlte/core';
	import { Environment, GLTF } from '@threlte/extras';
	const url = '3d/DamagedHelmet/glTF/DamagedHelmet.gltf';
</script>

<Environment path="/hdr/" files="stadium_01_2k.hdr" />
<PerspectiveCamera position={{ x: 5, y: 2, z: 5 }} fov={25}>
	<OrbitControls autoRotate enableDamping />
</PerspectiveCamera>
<DirectionalLight />
<GLTF {url} />
