<script>
    import { createEventDispatcher } from 'svelte';
    import { PaginationItem } from 'flowbite-svelte';

    export let page;
    export let totalPages;

    const dispatch = createEventDispatcher();

    const previousPage = () => {
        if (page > 1) {
            dispatch('previousPage');
        }
    };

    const nextPage = () => {
        if (page < totalPages) {
            dispatch('nextPage');
        }
    };
</script>

<div class="flex space-x-3 rtl:space-x-reverse">
    <PaginationItem large on:click={previousPage}>Anterior</PaginationItem>
    <PaginationItem large on:click={nextPage}>Siguiente</PaginationItem>
</div>
