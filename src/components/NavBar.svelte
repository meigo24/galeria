<script>
    import { NavBrand, Button, Input, NavHamburger } from 'flowbite-svelte';
    import { SearchOutline } from 'flowbite-svelte-icons';

    export let handleSearch;
</script>

<style>
    .header-container {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 20px 0;
    }
    .header-container .search-bar {
        margin-left: auto;
    }
</style>

<div class="header-container">
    <NavBrand href="/" class="title">
        <span class="self-center whitespace-nowrap text-2xl font-semibold dark:text-white">Galería de fotos</span>
    </NavBrand>
    <div class="flex md:order-2 search-bar">
        <div class="hidden relative md:block">
            <div class="flex absolute inset-y-0 start-0 items-center ps-3 pointer-events-none">
                <SearchOutline class="w-4 h-4" />
            </div>
            <Input id="search-navbar" class="ps-10" placeholder="Search..." on:input={handleSearch} />
        </div>
        <Button color="none" data-collapse-toggle="mobile-menu-3" aria-controls="mobile-menu-3" aria-expanded="false" class="md:hidden text-gray-500 dark:text-gray-400 hover:bg-gray-100 dark:hover:bg-gray-700 focus:outline-none focus:ring-4 focus:ring-gray-200 dark:focus:ring-gray-700 rounded-lg text-sm p-2.5 me-1">
            <SearchOutline class="w-5 h-5" />
        </Button>
        <NavHamburger />
    </div>
</div>
