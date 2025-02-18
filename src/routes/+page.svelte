<script lang="ts">
	import { SvelteFlow, Background, Controls, ControlButton, useNodes } from '@xyflow/svelte';
	import { PersistedState } from 'runed';
	import type { Node, Edge } from '@xyflow/svelte';
	import { generateCode } from '@nevthereal/random-utils';

	let nodes = $state.raw<Node[]>([
		{
			id: '1',
			position: { x: 0, y: 0 },
			data: { label: 'This' }
		},
		{
			id: '2',
			position: { x: 100, y: 100 },
			data: { label: 'Is cool' }
		}
	]);

	let edges = $state.raw<Edge[]>([{ id: '1-2', source: '1', target: '2' }]);

	function addNode() {
		nodes.push({ id: generateCode(5), position: { x: 0, y: 0 }, data: { label: 'Hi' } });
	}
</script>

<h1 class="my-4 text-center text-4xl font-bold">This is Svelte-Flow</h1>
<main class="mx-auto h-150 w-200">
	<SvelteFlow
		snapGrid={[25, 25]}
		fitViewOptions={{ nodes: nodes, minZoom: 50 }}
		bind:nodes
		bind:edges
	>
		<Background />
		<Controls showLock={false} />
	</SvelteFlow>
	<button onclick={addNode} class="rounded-xl bg-orange-500 p-2 font-bold text-white"
		>Add new Node</button
	>
</main>
