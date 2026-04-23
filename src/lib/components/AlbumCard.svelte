<script lang="ts">
	interface Props {
		title: string;
		artist: string;
		cover: string;
	}

	let { title, artist, cover }: Props = $props();
</script>

<div class="album-card group">
	<div class="cover-wrapper">
		<img src={cover} alt={title} />
		<div class="play-overlay">
			<button class="play-btn">
				<span class="material-symbols-outlined">play_arrow</span>
			</button>
		</div>
	</div>
	<h4>{title}</h4>
	<p>{artist}</p>
</div>

<style lang="scss">
	.album-card {
		cursor: pointer;

		.cover-wrapper {
			position: relative;
			aspect-ratio: 1 / 1;
			border-radius: 0.75rem;
			overflow: hidden;
			background-color: #19191f;
			margin-bottom: 1rem;
			transition: all 0.3s ease;

			img {
				width: 100%;
				height: 100%;
				object-fit: cover;
			}
		}

		&:hover .cover-wrapper {
			transform: scale(1.05);
			box-shadow: 0 20px 40px rgba(0, 0, 0, 0.6);
		}

		.play-overlay {
			position: absolute;
			inset: 0;
			background: rgba(0, 0, 0, 0.4);
			display: flex;
			align-items: center;
			justify-content: center;
			opacity: 0;
			transition: opacity 0.3s;
		}

		&:hover .play-overlay {
			opacity: 1;
		}

		.play-btn {
			width: 3.5rem;
			height: 3.5rem;
			background: #81ecff;
			color: #004d57;
			border: none;
			border-radius: 50%;
			display: flex;
			align-items: center;
			justify-content: center;
			transform: translateY(1rem);
			transition: transform 0.3s;

			span {
				font-variation-settings: "FILL" 1;
				font-size: 2rem;
			}
		}

		&:hover .play-btn {
			transform: translateY(0);
		}

		h4 {
			font-family: "Space Grotesk";
			font-weight: 700;
			font-size: 1.125rem;
			white-space: nowrap;
			overflow: hidden;
			text-overflow: ellipsis;
			margin: 0;
			transition: color 0.3s;
		}

		&:hover h4 {
			color: #81ecff;
		}

		p {
			font-size: 0.875rem;
			color: #acaab1;
			margin: 0.25rem 0 0 0;
		}
	}
</style>
