<script lang="ts">
	interface Props {
		title: string;
		artist: string;
		viewers: string;
		image: string;
		category: string;
	}

	let { title, artist, viewers, image, category }: Props = $props();
</script>

<div class="card group">
	<div class="thumbnail-wrapper">
		<img src={image} alt={title} loading="lazy" />

		<div class="badge-live">
			<span class="dot"></span>
			LIVE
		</div>

		<div class="viewer-count">
			{viewers}
		</div>

		<div class="overlay">
			<span class="material-symbols-outlined play-icon">play_circle</span>
		</div>
	</div>

	<div class="info">
		<h3>{title}</h3>
		<p>{artist} • {category}</p>
	</div>
</div>

<style lang="scss">
	.card {
		cursor: pointer;
	}

	.thumbnail-wrapper {
		position: relative;
		aspect-ratio: 16/9;
		border-radius: 1.25rem;
		overflow: hidden;
		background: #1f1f26;

		img {
			width: 100%;
			height: 100%;
			object-fit: cover;
			transition: transform 0.5s ease;
		}
	}

	.card:hover img {
		transform: scale(1.1);
	}

	.badge-live {
		position: absolute;
		top: 0.75rem;
		left: 0.75rem;
		background: #ff51fa;
		color: white;
		padding: 0.2rem 0.5rem;
		border-radius: 4px;
		font-size: 0.6rem;
		font-weight: 900;
		display: flex;
		align-items: center;
		gap: 0.25rem;

		.dot {
			width: 6px;
			height: 6px;
			background: white;
			border-radius: 50%;
			animation: pulse 1.5s infinite;
		}
	}

	.viewer-count {
		position: absolute;
		bottom: 0.75rem;
		right: 0.75rem;
		background: rgba(0, 0, 0, 0.6);
		backdrop-filter: blur(8px);
		padding: 0.25rem 0.5rem;
		border-radius: 8px;
		font-size: 0.65rem;
		color: rgba(255, 255, 255, 0.9);
	}

	.overlay {
		position: absolute;
		inset: 0;
		background: rgba(129, 236, 255, 0.2);
		display: flex;
		align-items: center;
		justify-content: center;
		opacity: 0;
		transition: opacity 0.3s;

		.play-icon {
			font-size: 3rem;
			color: white;
			transform: scale(0.8);
			transition: transform 0.3s;
		}
	}

	.card:hover .overlay {
		opacity: 1;
		.play-icon {
			transform: scale(1);
		}
	}

	.info {
		margin-top: 1rem;
		h3 {
			font-size: 1.1rem;
			font-weight: 700;
			margin: 0;
			transition: color 0.2s;
		}
		p {
			font-size: 0.85rem;
			color: #acaab1;
			margin-top: 0.25rem;
		}
	}

	.card:hover h3 {
		color: #81ecff;
	}

	@keyframes pulse {
		0% {
			opacity: 1;
		}
		50% {
			opacity: 0.3;
		}
		100% {
			opacity: 1;
		}
	}
</style>
