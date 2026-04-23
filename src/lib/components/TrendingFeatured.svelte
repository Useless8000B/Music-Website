<script lang="ts">
	let { children } = $props()
</script>

<section class="trending-section" id="trending-now">
	<div class="header">
		<div>
			<p class="tagline">The Pulse</p>
			<h2>Trending Now</h2>
		</div>
		<a href="/" class="view-charts">
			View Global Charts 
			<span class="material-symbols-outlined">trending_up</span>
		</a>
	</div>

	<div class="bento-grid">
		<div class="featured-card group">
			<img src="https://images.unsplash.com/photo-1470225620780-dba8ba36b745?q=80&w=2070&auto=format&fit=crop" alt="Viral Hits" />
			<div class="overlay"></div>
			<div class="content">
				<h3>Viral 50: Tokyo</h3>
				<p>The underground tracks breaking the internet this week.</p>
				<button class="play-btn">
					<span class="material-symbols-outlined">play_arrow</span>
				</button>
			</div>
		</div>

		<div class="track-list">
			{@render children()}
		</div>
	</div>
</section>

<style lang="scss">
	.trending-section {
		padding: 4rem;
		
		.header {
			display: flex;
			justify-content: space-between;
			align-items: flex-end;
			margin-bottom: 2.5rem;

			.tagline {
				color: #81ecff;
				text-transform: uppercase;
				font-size: 0.75rem;
				font-weight: 800;
				letter-spacing: 0.2em;
				font-family: 'Space Grotesk';
			}

			h2 {
				font-size: 2.5rem;
				font-family: 'Space Grotesk';
				font-weight: 800;
			}

			.view-charts {
				color: #81ecff;
				text-decoration: none;
				font-weight: bold;
				display: flex;
				align-items: center;
				gap: 0.5rem;
				transition: transform 0.2s;
				&:hover { transform: translateX(5px); }
			}
		}
	}

	.bento-grid {
		display: grid;
		grid-template-columns: 2fr 1.5fr;
		gap: 1.5rem;
	}

	.featured-card {
		position: relative;
		border-radius: 1.5rem;
		overflow: hidden;
		aspect-ratio: 16 / 9;

		img {
			width: 100%;
			height: 100%;
			object-fit: cover;
			transition: transform 0.5s;
		}

		&:hover img { transform: scale(1.05); }

		.overlay {
			position: absolute;
			inset: 0;
			background: linear-gradient(to top, rgba(0,0,0,0.9), transparent);
		}

		.content {
			position: absolute;
			bottom: 0;
			left: 0;
			padding: 2rem;

			h3 { font-size: 2rem; font-family: 'Space Grotesk'; font-weight: 900; }
			p { color: #cbd5e1; margin-bottom: 1rem; font-size: 0.9rem; }
		}
	}

	.play-btn {
		width: 3.5rem;
		height: 3.5rem;
		background: #fff;
		color: #000;
		border-radius: 50%;
		border: none;
		display: flex;
		align-items: center;
		justify-content: center;
		cursor: pointer;
		opacity: 0;
		transform: translateY(10px);
		transition: all 0.3s;
		
		span { font-variation-settings: 'FILL' 1; }
	}

	.featured-card:hover .play-btn {
		opacity: 1;
		transform: translateY(0);
	}

	.track-list {
		display: flex;
		flex-direction: column;
		gap: 1rem;
	}

	@media (max-width: 1024px) {
		.bento-grid { grid-template-columns: 1fr; }
	}
</style>