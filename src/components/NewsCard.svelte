<script>
    export let newsItem;    
    import {fade} from 'svelte/transition'
</script>

<div class="news_item" transition:fade={{duration: 1000}}>
    <img src="{newsItem?.imageUrl}" alt="">
    <h2>{newsItem?.title}</h2>
    <p class="author">By - {newsItem?.author} | {newsItem?.date} </p>
    <p>{newsItem?.content} </p>
    <a href="{newsItem?.readMoreUrl}" target="_blank" class="read-more">
        Read More
    </a>
</div>

<style>
    .news_item {
        display: inline;
        margin-bottom: 20px;
        padding: 12px;
        background-color: #fff;
        border-radius: 5px;
        box-shadow: rgba(17, 12, 46, 0.15) 0px 48px 100px 0px;
    }

    h2 {
        font-size: 2rem;
        font-family: 'Gideon Roman', cursive;
    }

    p {
        margin-top: 12px;
        font-size: 1.2rem;
    }

    .news_item img {
        width: 100%;
        max-height: 300px;
    }

    .news_item p.author {
        margin-top: 12px;
        color: #7897AB;
        font-size: 12px;
    }

    a {
        display: inline-block;
        margin-top: 12px;
        color: #00B4D8;
        text-decoration: none;
    }
    
</style>
