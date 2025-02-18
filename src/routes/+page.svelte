<script lang="ts">
	import { SvelteFlow, Background, Controls, ControlButton } from '@xyflow/svelte';
	import { PersistedState } from 'runed';
	import type { Node, Edge } from '@xyflow/svelte';

	const nodes = new PersistedState<Node[]>('nodes', [
		{
			id: '1', // required and needs to be a string
			position: { x: 0, y: 0 }, // required
			data: { label: 'hey' } // required
		},
		{
			id: '2',
			position: { x: 100, y: 100 },
			data: { label: 'world' }
		}
	]);
	const edges = new PersistedState<Edge[]>('edges', [{ id: '1-2', source: '1', target: '2' }]);
</script>

<main class="h-screen w-screen">
	<SvelteFlow bind:nodes={nodes.current} bind:edges={edges.current} fitView={true}>
		<Background />
		<Controls showLock={false}>
			<ControlButton onclick={() => console.log('⚡️')}>⚡️</ControlButton>
		</Controls>
	</SvelteFlow>
</main>
