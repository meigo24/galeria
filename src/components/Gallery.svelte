<script>
    export let photos = [];
</script>

<style>
    .gallery-grid {
        display: grid;
        gap: 10px;
    }
    .gallery-item img {
        width: 100%;
        height: auto;
        border-radius: 8px;
    }
</style>

<div class="gallery-grid grid-cols-2 md:grid-cols-3">
    {#each photos as photo}
        <div class="gallery-item">
            <img src={photo.src.large} alt={photo.alt} />
        </div>
    {/each}
</div>
