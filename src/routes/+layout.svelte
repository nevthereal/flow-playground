<script lang="ts">
	import '@xyflow/svelte/dist/style.css';
	import '../app.css';
	import { SvelteFlowProvider } from '@xyflow/svelte';
	let { children } = $props();
</script>

{@render children()}
