<script lang="ts">
	interface Props {
		title: string;
		artist: string;
		cover: string;
		duration: string;
		active?: boolean;
	}

	let { title, artist, cover, duration, active = false }: Props = $props();
</script>

<div class="queue-item {active ? 'active' : ''} group">
	<div class="cover-box">
		<img
			src={cover}
			alt={title}
			class={active ? "grayscale-0" : "grayscale group-hover:grayscale-0"}
		/>
		{#if active}
			<div class="playing-bars">
				<div class="bar bar-1"></div>
				<div class="bar bar-2"></div>
				<div class="bar bar-3"></div>
			</div>
		{/if}
	</div>
	<div class="info">
		<p class="title">{title}</p>
		<p class="artist">{artist}</p>
	</div>
	<span class="time">{duration}</span>
</div>

<style lang="scss">
	.queue-item {
		display: flex;
		align-items: center;
		gap: 1rem;
		padding: 1rem;
		border-radius: 1rem;
		transition: all 0.3s ease;
		cursor: pointer;

		&:hover:not(.active) {
			background-color: #25252d;
		}

		&.active {
			background-color: #1f1f26;
			border: 1px solid rgba(129, 236, 255, 0.2);
			box-shadow: 0 10px 20px rgba(0, 0, 0, 0.3);
		}

		.cover-box {
			position: relative;
			width: 3rem;
			height: 3rem;
			border-radius: 0.5rem;
			overflow: hidden;
			flex-shrink: 0;

			img {
				width: 100%;
				height: 100%;
				object-fit: cover;
				transition: all 0.5s;
			}
		}

		.info {
			flex: 1;
			overflow: hidden;
			.title {
				font-weight: 700;
				white-space: nowrap;
				overflow: hidden;
				text-overflow: ellipsis;
				margin: 0;
			}
			.artist {
				font-size: 0.75rem;
				color: #acaab1;
				margin: 0;
			}
		}

		&.active .artist {
			color: #81ecff;
			font-weight: 500;
		}

		.time {
			font-size: 0.75rem;
			color: #76747b;
			font-family: monospace;
		}

		.playing-bars {
			position: absolute;
			inset: 0;
			background: rgba(129, 236, 255, 0.2);
			display: flex;
			align-items: center;
			justify-content: center;
			gap: 2px;

			.bar {
				width: 3px;
				background: #81ecff;
				border-radius: 10px;
				animation: bounce 0.8s ease-in-out infinite alternate;
			}
			.bar-1 {
				height: 10px;
				animation-delay: 0.1s;
			}
			.bar-2 {
				height: 16px;
				animation-delay: 0.3s;
			}
			.bar-3 {
				height: 8px;
				animation-delay: 0.2s;
			}
		}
	}

	@keyframes bounce {
		from {
			transform: scaleY(0.5);
		}
		to {
			transform: scaleY(1.2);
		}
	}
</style>
