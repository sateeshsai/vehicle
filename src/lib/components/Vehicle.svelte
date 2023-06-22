<script lang="ts">
	import { AutoColliders, RigidBody, useRevoluteJoint } from '@threlte/rapier';
	import { T } from '@threlte/core';
	import { BoxGeometry, MeshStandardMaterial } from 'three';
	import { DEG2RAD } from 'three/src/math/MathUtils';
	import * as Three from 'three';
	import type { Vector3 } from 'three';

	export let anchor: Parameters<Vector3['set']> = [-1.2, -0.4, 0.8];

	import {
		MotorModel,
		type Collider as RapierCollider,
		type RigidBody as RapierRigidBody
	} from '@dimforge/rapier3d-compat';

	const { rigidBodyA, rigidBodyB, joint } = useRevoluteJoint(anchor, [0, 5, 6], [0, 0, 0]);

	// $: $joint?.configureMotorModel(MotorModel.AccelerationBased);
	// $: $joint?.configureMotorVelocity(1.0, 0.5);
</script>

<RigidBody type="dynamic" bind:rigidBody={$rigidBodyA}>
	<AutoColliders>
		<T.Mesh castShadow receiveShadow position={[0, 2, 2]} rotation={[90 * DEG2RAD, 0, 0]}>
			<T.CylinderGeometry args={[0.3, 0.3, 0.3]} />
			<T.MeshStandardMaterial color="blue" />
		</T.Mesh>
	</AutoColliders>
</RigidBody>

<RigidBody type="dynamic" bind:rigidBody={$rigidBodyB}>
	<AutoColliders>
		<T.Mesh castShadow receiveShadow position={[0, 2, 0]}>
			<T.BoxGeometry args={[2, 1, 1]} />
			<T.MeshStandardMaterial color="orange" />
		</T.Mesh>
	</AutoColliders>
</RigidBody>
