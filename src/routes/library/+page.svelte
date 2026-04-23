<script lang="ts">
	import LibraryCard from "$lib/components/LibraryCard.svelte";

	let activeTab = $state("Playlists");
	const tabs = ["Playlists", "Liked Songs", "Albums", "Artists"];

	const items = [
		{
			title: "Static Dreams",
			subtitle: "Vapor Theory • 2024",
			image: "https://images.unsplash.com/photo-1614613535308-eb5fbd3d2c17",
			shape: "square",
		},
		{
			title: "The Alchemist",
			subtitle: "Artist",
			image: "https://images.unsplash.com/photo-1508700115892-45ecd05ae2ad",
			shape: "circle",
		},
		{
			title: "Midnight Sun",
			subtitle: "Solaris • 2023",
			image: "https://images.unsplash.com/photo-1493225255756-d9584f8606e9",
			shape: "square",
		},
	] as const;
</script>

<div class="library-canvas">
	<header class="library-header">
		<div class="title-area">
			<h1>Library</h1>
			<p>Your personal sonic sanctuary. 4,281 tracks collected.</p>
		</div>
		<button class="btn-create">
			<span class="material-symbols-outlined">add_circle</span>
			Create Playlist
		</button>
	</header>

	<nav class="tabs">
		{#each tabs as tab}
			<button
				class:active={activeTab === tab}
				onclick={() => (activeTab = tab)}
			>
				{tab}
			</button>
		{/each}
	</nav>

	<div class="bento-grid">
		<section class="featured-liked">
			<div class="liked-card">
				<div class="content">
					<span class="material-symbols-outlined heart">favorite</span
					>
					<h2>Liked<br />Songs</h2>
					<p class="count">1,248 TRACKS</p>
				</div>
				<button class="floating-play">
					<span class="material-symbols-outlined">play_arrow</span>
				</button>
			</div>

			<div class="mini-list">
				<p class="label">Recent Likes</p>
				<div class="track-row">
					<img
						src="https://images.unsplash.com/photo-1614613535308-eb5fbd3d2c17"
						alt="cover"
					/>
					<div class="track-info">
						<span class="name">Digital Mirage</span>
						<span class="artist">Ether Echo</span>
					</div>
					<span class="material-symbols-outlined fav">favorite</span>
				</div>
			</div>
		</section>

		<section class="items-grid">
			{#each items as item}
				<LibraryCard {...item} />
			{/each}

			<button class="new-collection">
				<span class="material-symbols-outlined">add_box</span>
				<span>New Collection</span>
			</button>
		</section>
	</div>
</div>

<style lang="scss">
	.library-canvas {
		padding: 2rem 4rem;
		max-width: 1600px;
		margin: 0 auto;
	}

	.library-header {
		display: flex;
		justify-content: space-between;
		align-items: flex-end;
		margin-bottom: 3rem;
		h1 {
			font-size: 6rem;
			font-family: "Space Grotesk";
			font-weight: 900;
			line-height: 0.9;
			margin: 0;
			letter-spacing: -0.05em;
		}
		p {
			color: #acaab1;
			margin: 1rem 0 0 0;
		}
	}

	.btn-create {
		background: #00e3fd;
		color: #003840;
		border: none;
		padding: 1rem 1.5rem;
		border-radius: 99px;
		font-weight: 800;
		display: flex;
		align-items: center;
		gap: 0.5rem;
		cursor: pointer;
		transition: transform 0.2s;
		&:hover {
			transform: scale(1.05);
		}
	}

	.tabs {
		display: flex;
		gap: 2rem;
		border-bottom: 1px solid rgba(255, 255, 255, 0.1);
		margin-bottom: 3rem;
		button {
			background: none;
			border: none;
			color: #acaab1;
			padding-bottom: 1rem;
			font-family: "Space Grotesk";
			font-weight: 700;
			cursor: pointer;
			transition: all 0.3s;
			&.active {
				color: #81ecff;
				border-bottom: 2px solid #81ecff;
			}
		}
	}

	.bento-grid {
		display: grid;
		grid-template-columns: 1fr 2fr;
		gap: 2rem;
		@media (max-width: 1024px) {
			grid-template-columns: 1fr;
		}
	}

	.liked-card {
		background: linear-gradient(135deg, #7000ff, #ff51fa);
		border-radius: 2rem;
		padding: 2.5rem;
		height: 350px;
		position: relative;
		overflow: hidden;
		display: flex;
		flex-direction: column;
		justify-content: flex-end;

		.heart {
			font-size: 3rem;
			font-variation-settings: "FILL" 1;
			margin-bottom: 1rem;
		}

		h2 {
			font-size: 3.5rem;
			font-family: "Space Grotesk";
			line-height: 1;
			margin: 0;
		}

		.count {
			font-size: 0.75rem;
			font-weight: 800;
			letter-spacing: 0.2em;
			opacity: 0.8;
			margin-top: 0.5rem;
		}
	}

	.floating-play {
		position: absolute;
		bottom: 2rem;
		right: 2rem;
		width: 4rem;
		height: 4rem;
		background: white;
		border: none;
		border-radius: 50%;
		display: flex;
		align-items: center;
		justify-content: center;
		box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
		cursor: pointer;
		span {
			font-size: 2rem;
			font-variation-settings: "FILL" 1;
		}
	}

	.items-grid {
		display: grid;
		grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
		gap: 1.5rem;
	}

	.new-collection {
		border: 2px dashed rgba(172, 170, 177, 0.3);
		background: none;
		color: #acaab1;
		border-radius: 1.5rem;
		aspect-ratio: 1;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		gap: 1rem;
		cursor: pointer;
		transition: all 0.3s;
		&:hover {
			border-color: #81ecff;
			color: white;
		}
		span:first-child {
			font-size: 3rem;
		}
	}

	.mini-list {
		margin-top: 2rem;
		background: #19191f;
		padding: 1.5rem;
		border-radius: 2rem;
	}
	.track-row {
		display: flex;
		align-items: center;
		gap: 1rem;
		margin-top: 1rem;
		img {
			width: 40px;
			height: 40px;
			border-radius: 8px;
		}
		.track-info {
			flex: 1;
			display: flex;
			flex-direction: column;
		}
		.name {
			font-size: 0.85rem;
			font-weight: 700;
		}
		.artist {
			font-size: 0.75rem;
			color: #acaab1;
		}
		.fav {
			color: #ff51fa;
			font-size: 1rem;
			font-variation-settings: "FILL" 1;
		}
	}
</style>
