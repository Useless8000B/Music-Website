<script lang="ts">
	interface Props {
		title: string;
		subtitle: string;
		image: string;
		shape?: "square" | "circle";
		isPlaylist?: boolean;
	}

	let {
		title,
		subtitle,
		image,
		shape = "square",
		isPlaylist = false,
	}: Props = $props();
</script>

<div class="card-container group">
	<div
		class="image-wrapper {shape === 'circle'
			? 'rounded-full'
			: 'rounded-3xl'}"
	>
		<img src={image} alt={title} loading="lazy" />

		<div class="overlay">
			<button class="play-button">
				<span class="material-symbols-outlined">play_arrow</span>
			</button>
		</div>
	</div>

	<div class="info {shape === 'circle' ? 'text-center' : ''}">
		<h4>{title}</h4>
		<p class={shape === "circle" ? "artist-tag" : "subtitle"}>{subtitle}</p>
	</div>
</div>

<style lang="scss">
	.card-container {
		background: rgba(25, 25, 31, 0.4);
		padding: 1rem;
		border-radius: 1.5rem;
		transition: all 0.3s ease;
		cursor: pointer;

		&:hover {
			background: rgba(31, 31, 38, 0.8);
			.play-button {
				opacity: 1;
				transform: scale(1);
			}
		}
	}

	.image-wrapper {
		position: relative;
		aspect-ratio: 1;
		overflow: hidden;
		margin-bottom: 1rem;
		box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);

		img {
			width: 100%;
			height: 100%;
			object-fit: cover;
		}
	}

	.overlay {
		position: absolute;
		inset: 0;
		background: rgba(0, 0, 0, 0.2);
		opacity: 0;
		display: flex;
		align-items: center;
		justify-content: center;
		transition: opacity 0.3s ease;

		&:hover {
			opacity: 1;
		}
	}

	.play-button {
		width: 3rem;
		height: 3rem;
		background: #81ecff;
		color: #003840;
		border-radius: 50%;
		border: none;
		transform: scale(0.8);
		transition: all 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275);
		display: flex;
		align-items: center;
		justify-content: center;

		span {
			font-variation-settings: "FILL" 1;
		}
	}

	h4 {
		font-weight: 700;
		margin: 0;
		white-space: nowrap;
		overflow: hidden;
		text-overflow: ellipsis;
	}

	.subtitle {
		color: #acaab1;
		font-size: 0.75rem;
		margin-top: 0.25rem;
	}

	.artist-tag {
		color: #81ecff;
		font-size: 0.65rem;
		font-weight: 800;
		text-transform: uppercase;
		letter-spacing: 0.1em;
		margin-top: 0.25rem;
	}
</style>
