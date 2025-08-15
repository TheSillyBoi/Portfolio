<script lang="ts">
	export let data;

	/**
	 * @typedef {Object} Project
	 * @property {number} id
	 * @property {string} name
	 * @property {string} description
	 * @property {string} url
	 * @property {number} stars
	 * @property {string} updated
	 * @property {string|undefined} avatar_url
	 */
</script>

<h1 class="text-center text-[3rem] font-semibold text-[#cdd6f4] mt-7">My Projects</h1>

{#if data.error}
	<div class="text-center text-xl text-red-500">
		{data.error}
	</div>
{:else if data.projects.length === 0}
	<div class="text-center text-xl text-[#bac2de]">No projects found</div>
{:else}
	<div class="grid grid-cols-1 gap-7 p-2 md:grid-cols-2 lg:grid-cols-3 m-7">
		{#each data.projects as project}
			<div
				class="rounded-[.75rem] bg-[#585b70] p-4 text-center transition-colors hover:bg-[#45475a]"
			>
				<h2 class="mb-2 text-[2rem] text-[#cdd6f4]">
					{project.name}
				</h2>

				<p class="mb-4 text-[1.2rem] font-semibold text-[#a6adc8]">
					{project.description}
				</p>

				<div class="mb-4 flex items-center justify-center gap-4">
					<span class="text-yellow-300">
						⭐ {project.stars}
					</span>
				</div>

				<a
					href={project.url}
					target="_blank"
					rel="noopener noreferrer"
					class="inline-block rounded-lg bg-[#6c7086] px-4 py-2 font-semibold text-[#cdd6f4] transition-colors hover:bg-[#7f849c]"
				>
					View on GitHub
				</a>
			</div>
		{/each}
	</div>
{/if}
