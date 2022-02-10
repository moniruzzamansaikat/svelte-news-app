<script>
    export let news;
    import NewsCard from './NewsCard.svelte';
</script>

<div class="news_list">
    {#each news as newsItem}
        <NewsCard {newsItem} />
    {:else}
        <h2>Loading....</h2>
    {/each}
</div>

<style>
    .news_list {
        width: 100%;
        margin-top: 1rem;
        padding: 0;
        list-style: none;
        overflow: hidden;
        display: grid;
        grid-gap: 1em;
        grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
        grid-template-rows: masonry;
    }
</style>