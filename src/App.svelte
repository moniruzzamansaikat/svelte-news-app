<script>
	import News from './components/News.svelte';
	import Header from './components/Header.svelte';

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
			<h2 class="app-title">News Website</h2>
		</div>
	</div>
	<Header {categories} {activeCategory} on:setActiveCategory="{setActiveCategory}" />
	
	<div class="content">
		<News {news} />
	</div>
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

	.content {
		padding: 1rem;
		margin-top: 90px;
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