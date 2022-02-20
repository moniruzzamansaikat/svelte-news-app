<script>
    export let news;
    import NewsCard from './NewsCard.svelte';
    import Loading from './Loading.svelte';
</script>

<div class="news_list">
    {#each news as newsItem}
        <NewsCard {newsItem} />
    {:else}
        <Loading />
    {/each}
</div>

<style>
    .news_list {
        width: 100%;
        margin-top: 1rem;
        padding: 0;
        overflow: hidden;
        columns: 3;
        column-gap: 2rem;
        -webkit-columns: 3;
        -webkit-column-gap: 2rem;
    }

    @media screen and (max-width: 768px) {
        .news_list {
            columns: 2;
            -webkit-columns: 2;
        }
    }

    @media screen and (max-width: 600px) {
        .news_list {
            columns: 1;
            -webkit-columns: 1;
        }
    }
</style>