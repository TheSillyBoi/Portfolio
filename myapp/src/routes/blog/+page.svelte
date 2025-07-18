<script lang=ts>
    import Modal from "flowbite-svelte/Modal.svelte";
    import Button from "flowbite-svelte/Button.svelte";
    let defaultModal = $state(false);
</script>

<div class="text-center items-center justify-center text-[#cdd6f4]">
    <h1 class=" text-[2rem] font-bold">
        Welcome to my Blog
    </h1>


    <div class="gap-4 grid-cols-none grid items-center justify-center">

    <button onclick={() => (defaultModal = true)} class="max-w-[56rem] p-2 rounded-lg size-fit bg-[#45475a]">
            <h1 class="text-[1.5rem]">
                Why Simplicity Wins: The Case for Clean, Minimal Design
            </h1>
            <p class="line-clamp-3">
                In a world where every app and website seems to fight for your attention with flashy animations and cluttered layouts, there's something refreshing about simplicity. Minimal design isn't just an aesthetic choice — it's a way to make digital spaces more usable, more pleasant, and easier to navigate. Clean interfaces reduce mental fatigue and let users focus on what actually matters: the content.

I've noticed this firsthand while working on my own projects. Stripping away unnecessary elements and focusing on clear navigation always leads to a better experience. Whether you're building a personal blog, an online store, or a complex web app, simplicity isn't about sacrificing features — it's about making every feature count. Less clutter means more impact. Sometimes, the best way to stand out is by not trying too hard.
            </p>
        </button>

        <Modal title="Terms Of Service" headerClass="text-[#cdd6f4]" form bind:open={defaultModal} onaction={({ action }) => alert(`Handle "${action}"`)} class="text-[#bac2de] bg-[#585b70]">

            <p>
                With less than a month to go before the European Union enacts new consumer privacy laws for its citizens, companies around the world are updating their terms of service agreements to comply.
            </p>

            <p>
                The European Union's General Data Protection Regulation (G.D.P.R.) goes into effect on May 25 and is meant to ensure a common set of data rights in the European Union. It requires organizations to notify users as soon as possible of high-risk data breaches that could personally affect them.
            </p>
        
            {#snippet footer()}

                <Button type="submit" color="alternative">
                    Add a comment
                </Button>
            {/snippet}
        </Modal>

        <div id="example" class=" p-2 rounded-lg bg-[#45475a]">
            <h1>
                Hello
            </h1>
        </div>

    </div>
</div>