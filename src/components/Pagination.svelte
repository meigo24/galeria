<script>
    import { PaginationItem } from 'flowbite-svelte';

    export let previousPage;
    export let nextPage;
</script>

<div class="flex space-x-3 rtl:space-x-reverse">
    <PaginationItem large on:click={previousPage}>Anterior</PaginationItem>
    <PaginationItem large on:click={nextPage}>Siguiente</PaginationItem>
</div>
