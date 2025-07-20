<script lang="ts">
	import { enhance } from '$app/forms';
	import type { ActionData } from './$types';

	let { form }: { form: ActionData } = $props();

	import { onMount } from 'svelte';
	let container: HTMLDivElement;

	function setMinHeight() {
		const navbar = document.getElementById('global-navbar');
		if (navbar && container) {
			const navbarHeight = navbar.offsetHeight;
			container.style.minHeight = `calc(100vh - ${navbarHeight}px)`;
		}
	}

	onMount(() => {
		setMinHeight();
		window.addEventListener('resize', setMinHeight);
		return () => window.removeEventListener('resize', setMinHeight);
	});
</script>

<div bind:this={container} class=" flex items-center justify-center">
	<div class=" text-semibold rounded-[1.5rem] bg-[#45475a] px-12 py-8 text-center text-[#a6adc8]">
		<h1 class="text-[2rem] font-semibold">Login/Register</h1>
		<form method="post" action="?/login" use:enhance>
			<label class="text-[1.5rem]">
				Username
				<br />
				<input
					name="username"
					class="mt-1 rounded-md border border-gray-300 bg-white px-5 py-3 shadow-sm focus:border-blue-500 focus:ring-2 focus:ring-blue-500 focus:outline-none"
				/>
			</label>
			<br />
			<label class="text-[1.5rem]">
				Password
				<br />
				<input
					type="password"
					name="password"
					class="mt-1 rounded-md border border-gray-300 bg-white px-5 py-3 shadow-sm focus:border-blue-500 focus:ring-2 focus:ring-blue-500 focus:outline-none"
				/>
			</label>
			<br />
			<div class="py-4 text-center">
				<button
					class="float-left mx-2 max-w-22 min-w-22 rounded-md bg-blue-600 px-4 py-2 text-white transition hover:bg-blue-700"
				>
					Login
				</button>
				<button
					formaction="?/register"
					class=" float-right mx-2 max-w-22 min-w-22 rounded-md bg-blue-600 px-4 py-2 text-white transition hover:bg-blue-700"
				>
					Register
				</button>
			</div>
		</form>
		<p style="color: red">{form?.message ?? ''}</p>
	</div>
</div>
