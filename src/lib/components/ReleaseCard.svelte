<script lang="ts">
	interface Props {
		title: string;
		artist: string;
		cover: string;
		date?: string;
		type: "single" | "album";
	}

	let { title, artist, cover, date, type }: Props = $props();
</script>

<div class="release-card {type}">
	<div class="image-container">
		<img src={cover} alt={title} loading="lazy" />
		<button class="play-overlay">
			<span class="material-symbols-outlined">play_arrow</span>
		</button>
	</div>
	<div class="metadata">
		<h4>{title}</h4>
		<p class="artist">{artist}</p>
		{#if date}
			<p class="date">{date}</p>
		{/if}
	</div>
</div>

<style lang="scss">
	.release-card {
		cursor: pointer;
		transition: transform 0.3s ease;

		&:hover {
			transform: translateY(-4px);
			.play-overlay {
				opacity: 1;
				transform: translateY(0);
			}
		}

		.image-container {
			position: relative;
			overflow: hidden;
			background: #19191f;

			img {
				width: 100%;
				height: 100%;
				object-fit: cover;
				transition: transform 0.5s ease;
			}
		}

		/* Estilo específico para Singles (Aspecto Video/Retangular) */
		&.single .image-container {
			aspect-ratio: 16 / 9;
			border-radius: 0.75rem;
		}

		/* Estilo específico para Álbuns (Quadrado) */
		&.album .image-container {
			aspect-ratio: 1;
			border-radius: 1.5rem;
		}

		.play-overlay {
			position: absolute;
			bottom: 1rem;
			right: 1rem;
			background: #81ecff;
			color: #003840;
			border: none;
			padding: 0.75rem;
			border-radius: 50%;
			opacity: 0;
			transform: translateY(10px);
			transition: all 0.3s ease;
			display: flex;
			box-shadow: 0 8px 15px rgba(0, 0, 0, 0.3);
		}

		.metadata {
			margin-top: 1rem;
			h4 {
				font-weight: 700;
				margin: 0;
				white-space: nowrap;
				overflow: hidden;
				text-overflow: ellipsis;
			}
			.artist {
				color: #acaab1;
				font-size: 0.875rem;
				margin: 0.25rem 0;
			}
			.date {
				font-size: 0.65rem;
				color: #76747b;
				text-transform: uppercase;
				letter-spacing: 0.05em;
			}
		}
	}
</style>
