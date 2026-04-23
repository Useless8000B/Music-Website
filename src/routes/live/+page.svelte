<script lang="ts">
	import LiveCard from "$lib/components/LiveCard.svelte";

	const streams = [
		{
			title: "Electric Dreams Set",
			artist: "Luna Ray",
			viewers: "4.2K",
			category: "Techno",
			image: "https://images.unsplash.com/photo-1598387181032-a3103a2db5b3",
		},
		{
			title: "Warehouse Sessions",
			artist: "Ghost Protocol",
			viewers: "12.8K",
			category: "Industrial",
			image: "https://images.unsplash.com/photo-1574672280600-4accfa5b6f98",
		},
		{
			title: "Neon Lounge",
			artist: "Maya Chen",
			viewers: "890",
			category: "Lo-Fi Soul",
			image: "https://images.unsplash.com/photo-1514525253361-bee8a4874a73",
		},
		{
			title: "Studio 54 Reimagined",
			artist: "Various",
			viewers: "22.1K",
			category: "Disco House",
			image: "https://images.unsplash.com/photo-1470225620780-dba8ba36b745",
		},
	];
</script>

<div class="live-canvas">
	<section class="hero">
		<img
			src="https://images.unsplash.com/photo-1533174072545-7a4b6ad7a6c3"
			alt="Aura Vortex"
			class="hero-bg"
		/>
		<div class="hero-overlay"></div>

		<div class="hero-content">
			<div class="badges">
				<span class="live-now">LIVE NOW</span>
				<span class="viewers"
					><span class="material-symbols-outlined">visibility</span> 142.5K
					VIEWERS</span
				>
			</div>

			<h1>Aura Vortex</h1>
			<p class="desc">
				Experience the exclusive world tour debut of 'Synthetic Dreams'
				live from the Tokyo Dome.
			</p>

			<div class="actions">
				<button class="btn-primary">
					<span class="material-symbols-outlined">play_arrow</span>
					WATCH LIVE
				</button>
				<button class="btn-outline">ARTIST PROFILE</button>
			</div>
		</div>

		<div class="interaction-sidebar">
			<p class="label">LIVE INTERACTION</p>
			<div class="message">
				<span class="icon heart">favorite</span>
				<p><strong>Neo_Punk</strong> sent a Neon Heart!</p>
			</div>
			<div class="message">
				<span class="icon chat">chat</span>
				<p><strong>SynthLover</strong>: That drop was insane!</p>
			</div>
		</div>
	</section>

	<div class="content-wrapper">
		<section class="on-air">
			<div class="section-header">
				<h2>On Air Now</h2>
				<button class="view-all">View All Stages</button>
			</div>
			<div class="grid">
				{#each streams as stream}
					<LiveCard {...stream} />
				{/each}
			</div>
		</section>

		<div class="bottom-layout">
			<section class="schedule">
				<h2>Upcoming Schedule</h2>
				<div class="event-list">
					{#each [12, 15, 21] as day}
						<div class="event-item">
							<div class="date-box">
								<span class="month">OCT</span>
								<span class="day">{day}</span>
							</div>
							<div class="details">
								<h4>Cyberpunk Odyssey Festival</h4>
								<p>19:00 PST • Digital Mainstage</p>
							</div>
							<button class="reminder">
								<span class="material-symbols-outlined"
									>notifications</span
								>
								REMIND ME
							</button>
						</div>
					{/each}
				</div>
			</section>

			<aside class="side-content">
				<div class="trending">
					<h3>Trending Now</h3>
					<div class="tags">
						<span>#AuraVortexLive</span>
						<span>#NoirBeats</span>
						<span>#TokyoBass</span>
					</div>
				</div>

				<div class="community-cta">
					<h3>Join the Pulse Collective</h3>
					<p>Connect with fans globally in real-time hubs.</p>
					<button>OPEN COMMUNITY HUB</button>
				</div>
			</aside>
		</div>
	</div>
</div>

<style lang="scss">
	.live-canvas {
		padding: 2rem;
		max-width: 1600px;
		margin: 0 auto;
	}

	.hero {
		position: relative;
		height: 600px;
		border-radius: 2.5rem;
		overflow: hidden;
		display: flex;
		align-items: flex-end;
		padding: 4rem;

		.hero-bg {
			position: absolute;
			inset: 0;
			width: 100%;
			height: 100%;
			object-fit: cover;
			z-index: 1;
		}
		.hero-overlay {
			position: absolute;
			inset: 0;
			z-index: 2;
			background: linear-gradient(to top, #0e0e13, transparent 70%),
				linear-gradient(to right, rgba(14, 14, 19, 0.8), transparent);
		}
	}

	.hero-content {
		position: relative;
		z-index: 3;
		max-width: 600px;
		h1 {
			font-size: 6rem;
			line-height: 0.9;
			margin: 1.5rem 0;
			font-weight: 900;
			letter-spacing: -3px;
		}
		.desc {
			font-size: 1.1rem;
			color: #acaab1;
			margin-bottom: 2rem;
		}
	}

	.badges {
		display: flex;
		gap: 1rem;
		.live-now {
			background: #81ecff;
			color: #003840;
			padding: 0.25rem 0.75rem;
			border-radius: 99px;
			font-weight: 800;
			font-size: 0.7rem;
		}
		.viewers {
			display: flex;
			align-items: center;
			gap: 0.5rem;
			font-size: 0.8rem;
			color: white;
		}
	}

	.btn-primary {
		background: #81ecff;
		color: #003840;
		padding: 1rem 2rem;
		border-radius: 99px;
		border: none;
		font-weight: 800;
		cursor: pointer;
		display: inline-flex;
		align-items: center;
		gap: 0.5rem;
	}

	.interaction-sidebar {
		position: absolute;
		right: 4rem;
		bottom: 4rem;
		z-index: 3;
		background: rgba(25, 25, 31, 0.7);
		backdrop-filter: blur(20px);
		padding: 1.5rem;
		border-radius: 1.5rem;
		width: 300px;
		border: 1px solid rgba(255, 255, 255, 0.05);

		.label {
			font-size: 0.65rem;
			font-weight: 800;
			color: #81ecff;
			margin-bottom: 1rem;
			letter-spacing: 0.1em;
		}
		.message {
			display: flex;
			gap: 1rem;
			margin-bottom: 1rem;
			font-size: 0.75rem;
		}
		.icon {
			font-family: "Material Symbols Outlined";
			&.heart {
				color: #ff51fa;
			}
			&.chat {
				color: #81ecff;
			}
		}
	}

	.content-wrapper {
		margin-top: 4rem;
	}
	.section-header {
		display: flex;
		justify-content: space-between;
		align-items: flex-end;
		margin-bottom: 2rem;
	}
	.grid {
		display: grid;
		grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
		gap: 2rem;
	}

	.bottom-layout {
		display: grid;
		grid-template-columns: 2fr 1fr;
		gap: 4rem;
		margin-top: 6rem;
	}

	.event-item {
		display: flex;
		align-items: center;
		gap: 2rem;
		padding: 1.5rem;
		background: #131319;
		border-radius: 1.5rem;
		margin-bottom: 1rem;
		border: 1px solid transparent;
		transition: all 0.3s;

		&:hover {
			background: #19191f;
			border-color: rgba(129, 236, 255, 0.3);
		}

		.date-box {
			background: #1f1f26;
			padding: 1rem;
			border-radius: 1rem;
			display: flex;
			flex-direction: column;
			align-items: center;
			min-width: 70px;
			.month {
				font-size: 0.7rem;
				font-weight: 800;
				color: #acaab1;
			}
			.day {
				font-size: 1.5rem;
				font-weight: 900;
				color: #81ecff;
			}
		}

		.details {
			flex: 1;
			h4 {
				margin: 0;
				font-size: 1.25rem;
			}
			p {
				color: #acaab1;
				font-size: 0.9rem;
				margin: 0.25rem 0 0;
			}
		}
		.reminder {
			background: none;
			border: 1px solid #48474d;
			color: white;
			padding: 0.75rem 1.5rem;
			border-radius: 99px;
			cursor: pointer;
			display: flex;
			align-items: center;
			gap: 0.5rem;
			font-weight: 700;
			font-size: 0.7rem;
		}
	}

	.community-cta {
		background: linear-gradient(
			135deg,
			rgba(129, 236, 255, 0.1),
			rgba(255, 81, 250, 0.1)
		);
		padding: 2rem;
		border-radius: 2rem;
		border: 1px solid rgba(255, 255, 255, 0.05);
		h3 {
			margin-top: 0;
		}
		button {
			width: 100%;
			padding: 1rem;
			border-radius: 99px;
			border: none;
			background: white;
			font-weight: 800;
			cursor: pointer;
			margin-top: 1rem;
		}
	}

	.tags span {
		display: inline-block;
		padding: 0.5rem 1rem;
		background: #1f1f26;
		border-radius: 0.75rem;
		font-size: 0.8rem;
		margin: 0 0.5rem 0.5rem 0;
		cursor: pointer;
		&:hover {
			color: #81ecff;
		}
	}
</style>
