<script lang="ts">
  import { T } from "@threlte/core";
  import { ContactShadows, Float, Grid, OrbitControls } from "@threlte/extras";
  import { AutoColliders, RigidBody, Collider } from "@threlte/rapier";
  import { BoxGeometry, MeshStandardMaterial } from "three";
  import * as Three from "three";
  import Vehicle from "./Vehicle.svelte";
  import Raycar from "./Raycar.svelte";
  import { onMount } from "svelte";
  const { DEG2RAD } = Three.MathUtils;
  let innerWidth = 0;
  let innerHeight = 0;
  import { useLoader } from "@threlte/core";

  onMount(() => {
    console.log(innerWidth, innerHeight);
  });
  // import { useTexture } from '@threlte/extras';
  // const map = useTexture('/textures/road-dark.jpeg');
</script>

<svelte:window bind:innerWidth bind:innerHeight />

<T.PerspectiveCamera makeDefault castShadow position={[35, -10, 100]} fov={15}>
  <OrbitControls
    enableZoom={true}
    enableDamping
    autoRotateSpeed={0.5}
    target.y={1.5}
    minPolarAngle={Math.PI / 2.4}
    maxPolarAngle={Math.PI / 2.3}
  />
  <!-- minAzimuthAngle={Math.PI / 3} -->
</T.PerspectiveCamera>
<!-- position={[10, -10, 10]} -->
<!-- <T.OrthographicCamera makeDefault scale={2} fov={15}>
  <OrbitControls
    enableZoom={true}
    enableDamping
    autoRotateSpeed={0.5}
    target.y={1.5}
  />
</T.OrthographicCamera> -->

<!-- <T.DirectionalLight
  intensity={0.3}
  position.x={0}
  position.y={10}
  castShadow
  color="red"
/> -->

<T.PointLight
  intensity={0.5}
  position.x={0}
  position.y={20}
  position.z={10}
  castShadow
  color="#F9F871"
/>
<T.AmbientLight intensity={0.2} />

<T.Group position={[0, -10, 0]}>
  <Grid
    position.y={-0.001}
    cellColor="#ffffff"
    sectionColor="#ffffff"
    sectionThickness={0}
    fadeDistance={500}
    cellSize={1}
  />

  <!-- <RigidBody> -->
  <!-- <AutoColliders shape={'convexHull'}>
	<T.Mesh castShadow>
		<T.BoxGeometry args={[2, 2, 2]} />
		<T.MeshStandardMaterial color="blue" />
	</T.Mesh>
</AutoColliders> -->
  <!-- </RigidBody> -->
  <!-- <Vehicle /> -->
  <Raycar />
  <!-- <ContactShadows scale={10} blur={2} far={2.5} opacity={0.5} /> -->

  <AutoColliders shape={"cuboid"}>
    <T.Mesh receiveShadow rotation={[90 * DEG2RAD, 0, 0]}>
      <T.BoxGeometry args={[5000, 5000, 0.1]} />
      <T.MeshStandardMaterial color="#009EEE" side={Three.DoubleSide} />
    </T.Mesh>
  </AutoColliders>
  <!-- {#await map then value}
		{@const repeated = value.repeat.set(40, 40) || value}
		<T.Mesh receiveShadow rotation={[90 * DEG2RAD, 0, 0]}>
			<T.BoxGeometry args={[500, 500, 0.2]} />
			<T.MeshStandardMaterial map={value} repeat={true} />
		</T.Mesh>
	{/await} -->
  <!-- <RigidBody type={'fixed'}> -->
  <T.Group position={[innerWidth / 80, 5, 0]} rotation={[0, DEG2RAD * 110, 0]}>
    <Collider args={[5, 5, 5]} mass={1} shape={"cuboid"} type="dynamic" />
    <T.Mesh receiveShadow rotation={[0, 0, 0]}>
      <T.BoxGeometry args={[10, 10, 10]} />
      <T.MeshStandardMaterial transparent={true} />
    </T.Mesh>
  </T.Group>
  <T.Group position={[-innerWidth / 80, 5, 0]} rotation={[0, DEG2RAD * 110, 0]}>
    <Collider args={[5, 5, 5]} mass={1} shape={"cuboid"} type="dynamic" />
    <T.Mesh receiveShadow rotation={[0, 0, 0]}>
      <T.BoxGeometry args={[10, 10, 10]} />
      <T.MeshStandardMaterial transparent={true} />
    </T.Mesh>
  </T.Group>

  <!-- </RigidBody> -->

  <!-- <RigidBody type={'fixed'}>
	<Collider shape={'cuboid'} args={[-innerWidth / 100, 10, 10]} />
	<T.Mesh receiveShadow rotation={[0, 0, 0]} position={[-innerWidth / 80, 0, 0]}>
		<T.BoxGeometry args={[-innerWidth / 100, 10, 10]} />
		<T.MeshStandardMaterial color="yellow" side={Three.DoubleSide} />
	</T.Mesh>
</RigidBody> -->

  <!-- side={Three.DoubleSide}  -->

  <!-- 
<Float floatIntensity={1} floatingRange={[0, 1]}>
	<T.Mesh position.y={1.2} position.z={-0.75}>
		<T.BoxGeometry />
		<T.MeshStandardMaterial color="#0059BA" />
	</T.Mesh>
</Float>

<Float floatIntensity={1} floatingRange={[0, 1]}>
	<T.Mesh position={[1.2, 1.5, 0.75]} rotation.x={5} rotation.y={71}>
		<T.TorusKnotGeometry args={[0.5, 0.15, 100, 12, 2, 3]} />
		<T.MeshStandardMaterial color="#F85122" />
	</T.Mesh>
</Float>

<Float floatIntensity={1} floatingRange={[0, 1]}>
	<T.Mesh position={[-1.4, 1.5, 0.75]} rotation={[-5, 128, 10]}>
		<T.IcosahedronGeometry />
		<T.MeshStandardMaterial color="#F8EBCE" />
	</T.Mesh>
</Float> -->
</T.Group>
