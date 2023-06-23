<script lang="ts">
  import RaycastVehicleController from "./../RaycastVehicleController/RaycastVehicleController.svelte";
  import { OrbitControls } from "@threlte/extras";
  import { T } from "@threlte/core";
  import type { PerspectiveCamera } from "three";
  import { DEG2RAD } from "three/src/math/MathUtils";
  let carCam: PerspectiveCamera;
  import { GLTF } from "@threlte/extras";

  let camera = "car";
</script>

<RaycastVehicleController useAudio={false} steeringTorqueMultiplier={230}>
  <!-- <T.PerspectiveCamera
    bind:ref={carCam}
    slot="camera"
    rotation={[-90 * DEG2RAD, 75 * DEG2RAD, 90 * DEG2RAD]}
    fov={70}
    makeDefault={camera === "car"}
  >
    <OrbitControls
      enableZoom={true}
      enableDamping
      autoRotateSpeed={0.5}
      target.y={1.5}
    />
  </T.PerspectiveCamera> -->

  <T.Group slot="body" rotation.y={(-90 * Math.PI) / 180}>
    <!-- <T.Mesh castShadow>
      <T.BoxGeometry />
      <T.MeshStandardMaterial color="red" />
    </T.Mesh> -->
    <GLTF
      url="/models/fork/scene.gltf"
      rotation={[0, -90 * DEG2RAD, 0]}
      scale={1.2}
      position.y={-0.5}
    />
    <!-- <GLTF url="/models/fork/scene.gltf" /> -->
  </T.Group>
</RaycastVehicleController>
