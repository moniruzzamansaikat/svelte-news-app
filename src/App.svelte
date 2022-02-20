<script>
	import News from './components/News.svelte';
	import Header from './components/Header.svelte';
	import Footer from './components/Footer.svelte';

    let categories = ['all','technology','business','sports','world','politics','startup','entertainment','miscellaneous','hatke','science','automobile']
	let news = [];
    let activeCategory = 'all';

	const setActiveCategory = (e) => {
		activeCategory = e.detail;
	}

	$: fetch(`https://inshortsapi.vercel.app/news?category=${activeCategory}`)
		.then(res => res.json())
		.then(data => {
			document.title = `News | ${activeCategory}`;
			news = data.data;
		});


</script>

<main>
	<div class="app-bar">
		<div class="logo">
	        <img src="/img/logo.png" alt="">
			<h2 class="app-title">Newz Website</h2>
		</div>
	</div>
	<Header {categories} {activeCategory} on:setActiveCategory="{setActiveCategory}" />
	
	<div class="content">
		<News {news} />
	</div>

	{#if news.length > 0}
		<Footer />
	{/if}
</main> 
 
<style>
	.app-bar {
		background: #fff;
		height: 50px;
		position: fixed;
		width: 100%;
		top: 0;
		left: 0;
		display: flex;
		justify-content: center;
	}

	.app-bar .logo {
		display: flex;
		align-items: center;
	}
	
	.app-bar img {
		width: 60px;
	}
	
	.app-bar h2 {
        font-family: 'Gideon Roman', cursive;
		font-size: 2.2rem;
		margin: 0;
	}

	@media (max-width: 600px){ 
		.app-bar h2 {
			font-size: 1.5rem;
		}
	}

	.content {
		padding: 1rem;
		margin-top: 90px;
		padding-bottom: 4rem;
	}

	@media (max-width: 992px){ 
		.app-bar {
			height: 0 !important;
			z-index: 99999999;
		}

		.app-bar .logo {
			position: absolute;
			left: 0;
			top: 5px;
		}

		.content {
			margin-top: 50px;
		}
	}
</style>