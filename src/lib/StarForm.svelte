<script>
// @ts-nocheck
import EmptyStar from "./EmptyStar.svelte";
import FilledStar from "./FilledStar.svelte";
import { Card, Button } from "flowbite-svelte";

    let stars = [1, 2, 3, 4, 5];
    let rating = undefined;

    const changeRating = (i) => {
        rating = i + 1;
    };
</script>

<Card class="bg-gradient-to-r from-fuchsia-500 to-cyan-600">
    <h5 class="mb-1 text-2xl font-bold tracking-tight text-gray-900 text-white">Noteworthy technology acquisitions 2021</h5>

        <div class="grid grid-cols-5 w-2/3 mx-auto my-4">
            {#each stars as star, i}
            <!--filled stars-->
            {#if rating >= star}
            <button on:click={() => changeRating(i)}>
                <FilledStar/>
            </button>
            {/if}
            <!--not filled stars-->
            {#if rating < star}
            <button on:click={() => changeRating(i)}>
                <EmptyStar />
            </button>
            {/if}

            {#if rating === undefined}
            <button on:click={() => changeRating(i)}>
                <EmptyStar/>
                </button>
            {/if}
            {/each}
        </div>
        {#key rating} 
        {#if rating === undefined}
        <Button color="yellow" disabled="true">Submit</Button>
        {:else}
        <Button color="yellow">Submit</Button>
        {/if}
        {/key}
</Card>
