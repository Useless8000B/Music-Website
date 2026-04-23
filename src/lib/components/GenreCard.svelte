<script lang="ts">
	interface Props {
		title: string;
		img: string;
		icon: string;
		colorClass?: string;
	}

	let { title, img, icon, colorClass = "text-primary" }: Props = $props();
</script>

<div class="genre-card group">
	<img src={img} alt={title} class="genre-bg" />
	<div class="overlay"></div>
	<div class="content">
		<span class="material-symbols-outlined {colorClass}">{icon}</span>
		<h3>{title}</h3>
	</div>
</div>

<style lang="scss">
	.genre-card {
		position: relative;
		height: 12rem;
		border-radius: 0.75rem;
		overflow: hidden;
		cursor: pointer;
		transition: transform 0.3s ease;

		&:hover {
			transform: scale(1.02);
		}

		.genre-bg {
			position: absolute;
			inset: 0;
			width: 100%;
			height: 100%;
			object-fit: cover;
		}

		.overlay {
			position: absolute;
			inset: 0;
			background: linear-gradient(
				to top,
				rgba(14, 14, 19, 0.9) 10%,
				transparent 100%
			);
		}

		.content {
			position: absolute;
			inset: 0;
			padding: 1.5rem;
			display: flex;
			flex-direction: column;
			justify-content: flex-end;

			h3 {
				font-size: 1.5rem;
				font-weight: 900;
				font-family: "Space Grotesk";
				margin: 0;
			}

			span {
				margin-bottom: 0.5rem;
				font-size: 1.75rem;
			}
		}
	}
</style>
