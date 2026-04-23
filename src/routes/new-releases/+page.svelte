<script lang="ts">
	import ReleaseCard from '$lib/components/ReleaseCard.svelte';

	const singles = [
		{ title: 'Starlight Drift', artist: 'Luna & The Echoes', cover: 'https://images.unsplash.com/photo-1614613535308-eb5fbd3d2c17', type: 'single' },
		{ title: 'Midnight Protocol', artist: 'Ghost City', cover: 'https://images.unsplash.com/photo-1493225255756-d9584f8606e9', type: 'single' }
	] as const;

	const albums = [
		{ title: 'Solaris Voyage', artist: 'Sun Runner', cover: 'https://images.unsplash.com/photo-1459749411177-04218006d44d', date: 'OCT 24, 2023', type: 'album' },
		{ title: 'Digital Soul', artist: 'Binary Code', cover: 'https://images.unsplash.com/photo-1618005182384-a83a8bd57fbe', date: 'OCT 22, 2023', type: 'album' }
	] as const;
</script>

<div class="content-wrapper">
	<section class="hero">
		<div class="hero-bg">
			<img src="https://images.unsplash.com/photo-1550684848-fac1c5b4e853" alt="Cyber Pulse" />
			<div class="overlay"></div>
		</div>
		<div class="hero-body">
			<span class="tag">New Release</span>
			<h2>CYBER PULSE</h2>
			<p class="artist-name">The Neon Architects</p>
			<div class="btn-group">
				<button class="btn-primary">LISTEN NOW</button>
				<button class="btn-secondary">SAVE TO LIBRARY</button>
			</div>
		</div>
	</section>

	<section class="section">
		<div class="section-header">
			<h3>Fresh Singles</h3>
			<a href="/all">VIEW ALL</a>
		</div>
		<div class="horizontal-scroll scrollbar-hide">
			{#each singles as s}
				<div class="item"><ReleaseCard {...s} /></div>
			{/each}
		</div>
	</section>

	<section class="section">
		<div class="section-header">
			<h3>Latest Albums</h3>
		</div>
		<div class="album-grid">
			{#each albums as a}
				<ReleaseCard {...a} />
			{/each}
		</div>
	</section>
</div>

<style lang="scss">
	.content-wrapper { padding: 2rem; max-width: 1600px; margin: 0 auto; }

	.hero {
		position: relative;
		height: 500px;
		border-radius: 2rem;
		overflow: hidden;
		display: flex;
		align-items: flex-end;
		padding: 4rem;
		margin-bottom: 4rem;

		.hero-bg {
			position: absolute;
			inset: 0;
			z-index: -1;
			img { width: 100%; height: 100%; object-fit: cover; }
			.overlay { 
				position: absolute; inset: 0; 
				background: linear-gradient(to top, #0e0e13 0%, transparent 100%),
							linear-gradient(to right, #0e0e13 0%, transparent 50%);
			}
		}

		.tag { background: #ff51fa; color: white; padding: 0.25rem 0.75rem; border-radius: 99px; font-size: 0.6rem; font-weight: 800; text-transform: uppercase; }
		h2 { font-family: 'Space Grotesk'; font-size: 5rem; font-weight: 800; margin: 1rem 0; line-height: 0.8; }
		.artist-name { font-size: 1.5rem; color: #81ecff; font-style: italic; margin-bottom: 2rem; }
	}

	.btn-group { display: flex; gap: 1rem; }
	.btn-primary { background: #81ecff; color: #003840; font-weight: 800; padding: 1rem 2rem; border-radius: 99px; border: none; cursor: pointer; }
	.btn-secondary { background: rgba(255,255,255,0.1); backdrop-filter: blur(10px); color: white; border: 1px solid rgba(255,255,255,0.1); padding: 1rem 2rem; border-radius: 99px; cursor: pointer; }

	.horizontal-scroll { display: flex; gap: 1.5rem; overflow-x: auto; padding-bottom: 1rem; .item { min-width: 300px; } }
	
	.album-grid {
		display: grid;
		grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
		gap: 2rem;
	}

	.section-header {
		display: flex; justify-content: space-between; align-items: flex-end; margin-bottom: 2rem;
		h3 { font-size: 2rem; font-family: 'Space Grotesk'; margin: 0; }
		a { color: #81ecff; font-weight: 700; text-decoration: none; font-size: 0.875rem; }
	}
</style>