<script lang="ts">
  import Hero from '$lib/components/Hero.svelte';
    import TrackRow from '$lib/components/TrackRow.svelte';
    import TrendingFeatured from '$lib/components/TrendingFeatured.svelte';
</script>

<div class="home-wrapper">
  <Hero />
  <TrendingFeatured>
	<TrackRow 
		index="01" 
		title="Neon Nights" 
		artist="Synth City Collective" 
		img="https://images.unsplash.com/photo-1614613535308-eb5fbd3d2c17" 
	/>
	<TrackRow 
		index="02" 
		title="Electric Soul" 
		artist="Deep Orbit" 
		img="https://images.unsplash.com/photo-1493225255756-d9584f8606e9" 
	/>
	<TrackRow 
		index="03" 
		title="After Hours" 
		artist="The Midnight" 
		img="https://images.unsplash.com/photo-1459749411177-04218006d44d" 
	/>
</TrendingFeatured>
</div>

<style>
  .home-wrapper {
    padding-bottom: 100px; 
  }
</style>