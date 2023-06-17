<script>
	import { HTML } from '@threlte/extras';
	import { OrbitControls, PerspectiveCamera } from '@threlte/core';

	import { onDestroy } from 'svelte';
	import { spring } from 'svelte/motion';
	import { Color, GridHelper, MeshStandardMaterial, SphereBufferGeometry } from 'three';
	import { DEG2RAD } from 'three/src/math/MathUtils';
	import { AmbientLight, DirectionalLight, Mesh, useThrelte } from '@threlte/core';

	const getRandomColor = () => `#${Math.floor(Math.random() * 16777215).toString(16)}`;
	let material = new MeshStandardMaterial({
		color: new Color(getRandomColor()).convertSRGBToLinear()
	});
	const onClick = () => {
		material.color.set(getRandomColor());
		material = material;
	};
	let isHovering = false;
	let isPointerDown = false;
	const { scene } = useThrelte();
	const gridHelper = new GridHelper();

	scene.add(gridHelper);
	onDestroy(() => {
		scene.remove(gridHelper);
	});
	let htmlPosZ = spring(0);
	$: htmlPosZ.set(isPointerDown ? -0.15 : isHovering ? -0.075 : 0, {
		hard: isPointerDown
	});
</script>

<main />
<PerspectiveCamera position={{ x: 0, y: 0, z: 10 }} fov={25}>
	<OrbitControls enableDamping />
</PerspectiveCamera>
<!-- <HTML transform portal={document.body} center scale={1}>
	<div class="text-center bg-slate-900 w-full">
		<h1>Hello Hello</h1>
		<h1>Hello Hello Hello Hello</h1>
		<h1>Hello Hello</h1>
	</div>
</HTML> -->
<Mesh position={{ y: 0.5 }} geometry={new SphereBufferGeometry(0.5)} {material}>
	<HTML position={{ y: 1.25, z: $htmlPosZ }} transform>
		<button
			on:pointerenter={() => (isHovering = true)}
			on:pointerleave={() => {
				isPointerDown = false;
				isHovering = false;
			}}
			on:pointerdown={() => (isPointerDown = true)}
			on:pointerup={() => (isPointerDown = false)}
			on:pointercancel={() => {
				isPointerDown = false;
				isHovering = false;
			}}
			on:click={onClick}
			class="bg-slate-900 rounded-full px-3 text-white hover:opacity-90 active:opacity-70"
		>
			I'm a regular HTML button
		</button>
	</HTML>
	<AmbientLight intensity={0.3} />
	<HTML position="fixed" transform pointerEvents="stroke">
		<p
			class="text-xs w-auto translate-x-1/2 drop-shadow-lg"
			style="color: #{material.color.getHexString()}"
		>
			color: #{material.color.getHexString()}
		</p>
	</HTML>
</Mesh>
