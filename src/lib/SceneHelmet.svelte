<script>
	import {
		OrbitControls,
		DirectionalLight,
		Group,
		Object3DInstance,
		PerspectiveCamera,
		useFrame
	} from '@threlte/core';
	import { Environment, GLTF, HTML } from '@threlte/extras';
	const url = '3d/DamagedHelmet/glTF/DamagedHelmet.gltf';
	// const url = '3d/meetMat_exp/meetMat.gltf';
	// const url = '3d/paperCup/PaperCup.gltf';
</script>

<Environment path="/hdr/" files="stadium_01_2k.hdr" />
<!-- <Environment path="/hdr/" files="Eden_Diffuse8.hdr" /> -->
<PerspectiveCamera position={{ x: 5, y: 2, z: 5 }} fov={25}>
	<OrbitControls autoRotate enableDamping />
</PerspectiveCamera>
<DirectionalLight />
<!-- <GLTF {url} scale={0.2} position={{ x: 0, y: -1.35, z: 0 }} /> -->
<HTML transform position={{ x: 0, y: 0, z: -1.5 }} center sprite occlude>
	<h1>Hello World</h1>
</HTML>
<GLTF {url} scale={1.5} position={{ x: 0, y: -1.35, z: 0 }} />
