<script lang="ts">
	import Modal from 'flowbite-svelte/Modal.svelte';
	import Button from 'flowbite-svelte/Button.svelte';
	import snarkdown from 'snarkdown';
	import { onMount } from 'svelte';
	let modalStates = $state<boolean[]>([]);

	let data = $state<{
		entries: { Title: string; Content: string; PublishedDate: string }[];
	} | null>(null);


	$effect(() => {
		if (data) {
			$inspect(data);

			if (data.entries) {
				modalStates = Array(data.entries.length).fill(false);
				for (let i in data.entries) {
					$inspect(i);
				}
			} else {
				console.log('an error has occurred');
			}
		}
	});

	onMount(async () => {
		const response = await fetch("https://raw.githubusercontent.com/TheSillyBoi/Portfolio/refs/heads/main/myapp/src/routes/blog/blog.json");
		data = await response.json();
		console.log(data);
	});
</script>

<div class="items-center justify-center text-center text-[#cdd6f4]">
	<h1 class="m-10 text-[2rem] font-bold">Welcome to my Blog</h1>
	<div class="grid grid-cols-none items-center text-left justify-center gap-4">
		{#each data?.entries ?? [] as entry, index}
			<!-- svelte-ignore event_directive_deprecated -->
			<button
				on:click={() => (modalStates[index] = true)}
				class="size-fit max-w-[56rem] min-w-[56rem] rounded-lg bg-[#45475a] p-2"
			>
				{#if entry?.Title}
					<h1>{entry.Title}({entry.PublishedDate})</h1>
				{:else}
					<p>No title available</p>
				{/if}
				<div class="line-clamp-3">
					{@html snarkdown(entry.Content)}
				</div>
			</button>
			{#if index < modalStates.length}
				<Modal
					title={entry.Title}
					classes={{ header: 'text-[#cdd6f4]' }}
					size="lg"
					form
					bind:open={modalStates[index]}
					onaction={({ action }) => alert(`Handle "${action}"`)}
					class="bg-[#45475a] text-[#bac2de] "
					><h1>{@html snarkdown(entry?.Content)}</h1>
					<!-- <Button type="submit" color="alternative">Add a comment</Button> -->
				</Modal>
			{/if}
		{/each}
	</div>
</div>
