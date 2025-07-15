<script lang="ts">
	import { enhance } from '$app/forms';
	import type { ActionData } from './$types';

	let { form }: { form: ActionData } = $props();
</script>
<div class="h-screen  text-center align-middle">
	<div class='inline-block p-4 bg-[#45475a] rounded-[1.5rem]  text-center '>
		<h1>
			Login/Register
		</h1>
		<form method="post" action="?/login" use:enhance>
			<label>
				Username
				<br>
				<input
					name="username"
					class="mt-1 rounded-md border border-gray-300 bg-white px-3 py-2 shadow-sm focus:border-blue-500 focus:ring-2 focus:ring-blue-500 focus:outline-none"
			/>
			</label>
			<br>
			<label>
				Password
			<br>
				<input
					type="password"
					name="password"
					class="mt-1 rounded-md border border-gray-300 bg-white px-3 py-2 shadow-sm focus:border-blue-500 focus:ring-2 focus:ring-blue-500 focus:outline-none"
			/>
			</label>
			<br>
			<div class="text-center py-4">
				<button class="float-left rounded-md max-w-22 min-w-22 bg-blue-600 px-4 py-2 mx-2 text-white transition hover:bg-blue-700">
					Login
				</button>
				<button
					formaction="?/register"
					class=" float-right rounded-md bg-blue-600 px-4 py-2 max-w-22 min-w-22 mx-2 text-white transition hover:bg-blue-700">
					Register
				</button>
			</div>
		</form>
	<p style="color: red">{form?.message ?? ''}</p>
	</div>
</div>