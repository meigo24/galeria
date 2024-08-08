<script>
    import { Button } from 'flowbite-svelte';

    export let handleCategoryClick;
</script>

<style>
    .button-container {
        display: flex;
        justify-content: center;
        flex-wrap: wrap;
        gap: 10px;
        padding: 20px 0;
    }
</style>

<div class="button-container">
    <Button pill size="xl" outline on:click={() => handleCategoryClick('all categories')}>All categories</Button>
    <Button pill size="xl" color="alternative" on:click={() => handleCategoryClick('flowers')}>Flowers</Button>
    <Button pill size="xl" color="alternative" on:click={() => handleCategoryClick('mountains')}>Mountains</Button>
    <Button pill size="xl" color="alternative" on:click={() => handleCategoryClick('galaxies')}>Galaxies</Button>
    <Button pill size="xl" color="alternative" on:click={() => handleCategoryClick('cats')}>Cats</Button>
    <Button pill size="xl" color="alternative" on:click={() => handleCategoryClick('food')}>Food</Button>
</div>
