<script lang="ts">
	import { enhance } from '$app/forms';
	//  import type { ActionData } from './$types';

	// let { form }: { form: ActionData } = $props();

	import { onMount } from 'svelte';
	let container: HTMLDivElement;

	function setMinHeight() {
		const navbar = document.getElementById('global-navbar');
		if (navbar && container) {
			const navbarHeight = navbar.offsetHeight;
			container.style.minHeight = `calc(100vh - ${navbarHeight}px - 6rem)`;
		}
	}

	onMount(() => {
		setMinHeight();

		window.addEventListener('resize', setMinHeight);
		return () => window.removeEventListener('resize', setMinHeight);
	});
</script>

<form></form>
<div>
	<h1
		class="text-bold m-1 flex w-full flex-nowrap justify-center text-center text-[3rem] text-[#cdd6f4]"
	>
		If you want to contact me, I'm active on the following platforms:
	</h1>

	<div bind:this={container} class="flex flex-wrap items-center justify-center text-center">
		<div class=" rounded-xl bg-[#45475a] px-6 py-3 text-center text-[#89b4fa]">
			<div class="text-left text-[4rem]">
				<a href="https://bsky.app/profile/thesillyb0y.bsky.social" target="_blank">
					<i class="fa-brands fa-bluesky px-4"> </i>
					@thesillyb0y.bsky.social
				</a>
				<br />

				<a href="https://github.com/thesillyboi" target="_blank">
					<i class="fa-brands fa-github px-4"> </i>
					@TheSillyBoi
				</a>
				<br />

				<a href="https://www.reddit.com/user/MisterMonkeee/" target="_blank">
					<i class="fa-brands fa-reddit px-4"> </i>
					@TheSillyBoi
				</a>
				<br />

				<a href="https://steamcommunity.com/profiles/76561199097336926/" target="_blank">
					<i class="fa-brands fa-steam px-4"> </i>
					@TheMonkeyBoi
				</a>
				<br />
			</div>
		</div>
	</div>
</div>
