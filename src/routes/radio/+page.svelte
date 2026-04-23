<script lang="ts">
	import QueueItem from '$lib/components/QueueItem.svelte';

	const queue = [
		{ title: 'Electric Dreams', artist: 'Synthetic Soul Project', cover: 'https://images.unsplash.com/photo-1614613535308-eb5fbd3d2c17', duration: '3:42', active: true },
		{ title: 'Vapor Trails', artist: 'Neon District', cover: 'https://images.unsplash.com/photo-1493225255756-d9584f8606e9', duration: '4:15' },
		{ title: 'Digital Horizon', artist: 'Cyberwave Collective', cover: 'https://images.unsplash.com/photo-1614613535308-eb5fbd3d2c17', duration: '2:58' }
	];
</script>

<main class="player-canvas">
	<div class="glow primary-glow"></div>
	<div class="glow secondary-glow"></div>

	<div class="layout-grid">
		<section class="artwork-column">
			<div class="main-cover-wrapper">
				<div class="glow-underlay"></div>
				<img src="https://images.unsplash.com/photo-1614613535308-eb5fbd3d2c17?q=80&w=1000" alt="Cover" />
				<div class="badge">ULTRA HD</div>
			</div>

			<div class="track-header">
				<div class="titles">
					<h1>Electric Dreams</h1>
					<p class="artist">Synthetic Soul Project</p>
				</div>
				<div class="actions">
					<button class="icon-btn"><span class="material-symbols-outlined">favorite</span></button>
					<button class="icon-btn"><span class="material-symbols-outlined">share</span></button>
				</div>
			</div>

			<p class="description">
				Experience the pulse of the future with <strong>Synthetic Soul Project's</strong> latest editorial release. 
				A masterclass in neon-drenched soundscapes.
			</p>
		</section>

		<section class="queue-column">
			<div class="queue-container">
				<div class="header">
					<h2>Up Next</h2>
					<span class="badge-autoplay">AUTO-PLAY ON</span>
				</div>

				<div class="list scrollbar-hide">
					{#each queue as item}
						<QueueItem {...item} />
					{/each}
				</div>

				<div class="upgrade-card">
					<span class="material-symbols-outlined bolt">bolt</span>
					<h3>Unlock Lossless Audio</h3>
					<p>Experience every bit of detail.</p>
					<button>Upgrade Pro</button>
				</div>
			</div>
		</section>
	</div>
</main>

<style lang="scss">
	.player-canvas {
		min-height: 100vh;
		padding: 6rem 2rem 8rem 2rem;
		position: relative;
		overflow: hidden;
	}

	.glow {
		position: absolute;
		border-radius: 50%;
		filter: blur(120px);
		z-index: 0;
		pointer-events: none;
	}
	.primary-glow { top: 20%; left: 30%; width: 500px; height: 500px; background: rgba(129, 236, 255, 0.1); }
	.secondary-glow { bottom: 10%; right: 10%; width: 400px; height: 400px; background: rgba(255, 81, 250, 0.08); }

	.layout-grid {
		display: grid;
		grid-template-columns: 1fr;
		gap: 3rem;
		position: relative;
		z-index: 1;
		max-width: 1300px;
		margin: 0 auto;

		@media (min-width: 1024px) {
			grid-template-columns: 7fr 5fr;
		}
	}

	.main-cover-wrapper {
		position: relative;
		max-width: 540px;
		aspect-ratio: 1;
		border-radius: 2rem;
		background: #19191f;
		
		img { width: 100%; height: 100%; object-fit: cover; border-radius: 2rem; position: relative; z-index: 2; border: 1px solid rgba(255,255,255,0.05); }
		
		.glow-underlay { position: absolute; inset: -20px; background: linear-gradient(45deg, #81ecff, #ff51fa); filter: blur(40px); opacity: 0.3; }
		
		.badge {
			position: absolute; top: -1rem; right: -1rem; background: #a900a9; color: white;
			padding: 0.5rem 1rem; border-radius: 0.75rem; font-weight: 900; font-family: 'Space Grotesk';
			font-size: 0.75rem; transform: rotate(12deg); z-index: 3; box-shadow: 0 10px 20px rgba(0,0,0,0.5);
		}
	}

	.track-header {
		margin-top: 2.5rem;
		display: flex;
		justify-content: space-between;
		align-items: flex-end;
		
		h1 { font-size: clamp(2.5rem, 5vw, 4rem); font-weight: 900; font-family: 'Space Grotesk'; line-height: 0.9; margin: 0; }
		.artist { font-size: 1.5rem; color: #81ecff; font-family: 'Space Grotesk'; margin-top: 0.5rem; }
	}

	.queue-container {
		background: #131319;
		border-radius: 2rem;
		padding: 2rem;
		height: 100%;
		display: flex;
		flex-direction: column;
		gap: 1.5rem;

		.list { overflow-y: auto; flex: 1; display: flex; flex-direction: column; gap: 0.5rem; }
	}

	.upgrade-card {
		background: linear-gradient(135deg, #7000ff 0%, #a900a9 100%);
		padding: 1.5rem;
		border-radius: 1.5rem;
		position: relative;
		overflow: hidden;
		
		h3 { font-family: 'Space Grotesk'; font-weight: 800; font-size: 1.25rem; margin-bottom: 0.25rem; }
		p { font-size: 0.75rem; opacity: 0.8; margin-bottom: 1rem; }
		button { background: white; color: #7000ff; border: none; padding: 0.5rem 1rem; border-radius: 99px; font-weight: 800; font-size: 0.7rem; text-transform: uppercase; }
		
		.bolt { position: absolute; right: -1rem; bottom: -1rem; font-size: 6rem; opacity: 0.15; }
	}
</style>