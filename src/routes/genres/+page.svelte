<script lang="ts">
	import GenreCard from '$lib/components/GenreCard.svelte';
	import AlbumCard from '$lib/components/AlbumCard.svelte';

	const genres = [
		{ title: 'Electronic', icon: 'electric_bolt', img: 'https://images.unsplash.com/photo-1550745165-9bc0b252726f', color: 'text-primary' },
		{ title: 'Hip Hop', icon: 'speaker', img: 'https://images.unsplash.com/photo-1493225255756-d9584f8606e9', color: 'text-secondary' },
		{ title: 'Jazz', icon: 'settings_input_component', img: 'https://images.unsplash.com/photo-1511192336575-5a79af67a629', color: 'text-tertiary' },
		{ title: 'Rock', icon: 'skull', img: 'https://images.unsplash.com/photo-1498038432885-c6f3f1b912ee', color: 'text-error' }
	];

	const recommendations = [
		{ title: 'Neon Horizons', artist: 'Digital Pulse', cover: 'https://images.unsplash.com/photo-1614613535308-eb5fbd3d2c17' },
		{ title: 'Echo Chamber', artist: 'Lila Vance', cover: 'https://images.unsplash.com/photo-1614613535308-eb5fbd3d2c17' }
	];
</script>

<div class="explore-container">
	<section class="search-section">
		<div class="search-box">
			<span class="material-symbols-outlined">search</span>
			<input type="text" placeholder="Artists, songs, or podcasts" />
		</div>
	</section>

	<section class="grid-section">
		<div class="section-header">
			<h2>Explore Genres</h2>
			<button>View All</button>
		</div>
		<div class="genre-grid">
			{#each genres as genre}
				<GenreCard {...genre} colorClass={genre.color} />
			{/each}
		</div>
	</section>

	<section class="recommendations">
		<div class="section-header">
			<h2>Recommended for You</h2>
		</div>
		<div class="album-grid">
			{#each recommendations as album}
				<AlbumCard {...album} />
			{/each}
		</div>
	</section>
</div>

<style lang="scss">
	.explore-container {
		padding: 2rem;
		max-width: 1200px;
		margin: 0 auto;
	}

	.section-header {
		display: flex;
		justify-content: space-between;
		align-items: center;
		margin-bottom: 2rem;
		h2 { font-size: 2.5rem; font-weight: 900; font-family: 'Space Grotesk'; }
		button { color: #81ecff; background: none; border: none; font-weight: bold; cursor: pointer; text-transform: uppercase; font-size: 0.8rem; }
	}

	.genre-grid {
		display: grid;
		grid-template-columns: repeat(auto-fill, minmax(240px, 1fr));
		gap: 1.5rem;
		margin-bottom: 4rem;
	}

	.album-grid {
		display: grid;
		grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
		gap: 2rem;
	}

	.search-box {
		background: #25252d;
		padding: 1.25rem 2rem;
		border-radius: 9999px;
		display: flex;
		align-items: center;
		gap: 1rem;
		margin-bottom: 3rem;
		input { background: none; border: none; color: white; width: 100%; outline: none; font-size: 1.1rem; }
		span { color: #76747b; }
	}
</style>