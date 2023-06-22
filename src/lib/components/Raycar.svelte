<script>
	import RaycastVehicleController from './../RaycastVehicleController/RaycastVehicleController.svelte';
	import { T } from '@threlte/core';
	import { BoxGeometry } from 'three';
	import { DEG2RAD } from 'three/src/math/MathUtils';
	let carCam;

	let camera = 'car';
</script>

<RaycastVehicleController useAudio={false} steeringTorqueMultiplier={230}>
	<!-- <T.PerspectiveCamera
		bind:ref={carCam}
		slot="camera"
		rotation={[-90 * DEG2RAD, 75 * DEG2RAD, 90 * DEG2RAD]}
		fov={70}
		makeDefault={camera === 'car'}
	/> -->

	<T.Group slot="body" rotation.y={(-90 * Math.PI) / 180}>
		<T.Mesh castShadow>
			<T.BoxGeometry />
			<T.MeshStandardMaterial color="red" />
		</T.Mesh>
	</T.Group>
</RaycastVehicleController>
