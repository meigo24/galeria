<script>
    import axios from 'axios';
    import { onMount } from 'svelte';
    import NavBar from './components/NavBar.svelte';
    import CategoryButtons from './components/CategoryButtons.svelte';
    import Gallery from './components/Gallery.svelte';
    import Pagination from './components/Pagination.svelte';

    let data = { photos: [] };
    let query = 'nature,fruits';
    let page = 1;
    let totalPages = 1;

    const API_URL = "https://api.pexels.com/v1/search";
    const API_KEY = 'OHkyiNwV7RmQoWX14KnbTHOVkxobOYICciV0S6Nndf51BJTFEkKPitge';

    const fetchPhotos = async () => {
        try {
            const response = await axios.get(API_URL, {
                headers: {
                    Authorization: API_KEY
                },
                params: {
                    query,
                    per_page: 15,
                    page
                }
            });
            data = response.data;
            totalPages = Math.ceil(response.data.total_results / 15);
        } catch (error) {
            console.error('Error fetching images:', error);
        }
    };

    const handleSearch = async (event) => {
        query = event.target.value;
        page = 1;
        await fetchPhotos();
    };

    const handleCategoryClick = async (category) => {
        query = category;
        page = 1;
        await fetchPhotos();
    };

    const handlePreviousPage = async () => {
        if (page > 1) {
            page--;
            await fetchPhotos();
        }
    };

    const handleNextPage = async () => {
        if (page < totalPages) {
            page++;
            await fetchPhotos();
        }
    };

    onMount(fetchPhotos);
</script>

<style>
    .main-container {
        margin: 0 20px;
    }
</style>

<div class="main-container">
    <NavBar on:search={handleSearch} />
    <CategoryButtons on:categoryClick={handleCategoryClick} />
    <Gallery {photos}={data.photos} />
    <Pagination {page} {totalPages} on:previousPage={handlePreviousPage} on:nextPage={handleNextPage} />
</div>
