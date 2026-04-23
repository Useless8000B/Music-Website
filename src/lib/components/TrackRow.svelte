<script lang="ts">
	let { title, artist, img, index } = $props();
</script>

<div class="track-row group">
	<div class="img-container">
		<img src={img} alt={title} />
		<div class="hover-play">
			<span class="material-symbols-outlined">play_arrow</span>
		</div>
	</div>
	<div class="info">
		<h4>{title}</h4>
		<p>{artist}</p>
	</div>
	<span class="rank">{index}</span>
</div>

<style lang="scss">
	.track-row {
		background: #19191f;
		padding: 1rem;
		border-radius: 1rem;
		display: flex;
		align-items: center;
		gap: 1rem;
		transition: background 0.3s;
		cursor: pointer;

		&:hover { background: #25252d; }

		.img-container {
			position: relative;
			width: 4rem;
			height: 4rem;
			border-radius: 0.5rem;
			overflow: hidden;
			flex-shrink: 0;

			img { width: 100%; height: 100%; object-fit: cover; }
			
			.hover-play {
				position: absolute;
				inset: 0;
				background: rgba(0,0,0,0.5);
				display: flex;
				align-items: center;
				justify-content: center;
				opacity: 0;
				transition: opacity 0.2s;
				span { color: white; font-variation-settings: 'FILL' 1; }
			}
		}

		&:hover .hover-play { opacity: 1; }

		.info {
			flex: 1;
			h4 { margin: 0; font-family: 'Space Grotesk'; font-weight: 700; }
			p { margin: 0; font-size: 0.75rem; color: #94a3b8; }
		}

		.rank {
			color: #81ecff;
			font-family: 'Space Grotesk';
			font-weight: 800;
			font-size: 0.8rem;
		}
	}
</style>