<script>
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

<h1 class="text-center text-[4rem] font-semibold text-[#cdd6f4]">

    My Projects

</h1>


{#if data.error}

    <div class="text-center text-red-500 text-xl">

        {data.error}

    </div>

{:else if data.projects.length === 0}

    <div class="text-center text-[#bac2de] text-xl">

        No projects found

    </div>

{:else}

    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-15 p-6">

        {#each /** @type {Project[]} */ (data.projects) as project}

            <div class="bg-[#585b70] rounded-[1.5rem] p-6 text-center hover:bg-[#45475a] transition-colors">
                
                <h2 class="text-[2rem] mb-2 text-[#cdd6f4]">
                    {project.name}
                </h2>

                <p class="text-[1.2rem] mb-4 font-semibold text-[#a6adc8]">
                    {project.description}
                </p>

                <div class="flex justify-center items-center gap-4 mb-4">

                    <span class="text-yellow-300">

                        ⭐ {project.stars}

                    </span>

                </div>

                <a 
                    href={project.url} 
                    target="_blank" 
                    rel="noopener noreferrer"
                    class="bg-[#6c7086] hover:bg-[#89b4fa] px-4 py-2 rounded-lg transition-colors inline-block text-[#cdd6f4] font-semibold"
                >

                    View on GitHub

                </a>

            </div>

        {/each}

    </div>

{/if}

