<script lang="ts">
	let element: HTMLElement;
	let num: number = 10;

	function mutate(node: HTMLElement) {
		function callback(mutations: MutationRecord[]) {
			console.log(mutations);
		}

		const observer = new MutationObserver(callback);

		console.log('Observing', node);
		observer.observe(node, { childList: true, subtree: true });
	}
</script>

<button on:click={() => num++}>Add item</button>

<div bind:this={element} use:mutate>
	{#each [...Array(num).keys()] as i}
		<div>
			{i}
		</div>
	{/each}
</div>
