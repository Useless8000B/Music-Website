<script lang="ts">
    import favicon from '$lib/assets/favicon.svg';
    import Sidebar from '$lib/components/Sidebar.svelte';
    import { page } from '$app/state';
    import Topbar from '$lib/components/Topbar.svelte';

    let { children } = $props();
    let sidebarOpen = $state(false);

    const toggleSidebar = () => (sidebarOpen = !sidebarOpen);
</script>

<svelte:head>
    <link rel="icon" href={favicon} />
    <link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@300;700;900&family=Manrope:wght@300;400;700&display=swap" rel="stylesheet"/>
    <link href="https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined:wght,FILL@100..700,0..1&display=swap" rel="stylesheet" />
</svelte:head>

<Topbar {toggleSidebar}/>

<div class="app-layout">
    <Sidebar activeRoute={page.url.pathname} isOpen={sidebarOpen}/>

    <main class="main-content">
        {@render children()}
    </main>
</div>

<style>
    :global(body) {
        margin: 0;
        background-color: #0e0e13;
        color: #f9f5fd;
        font-family: 'Manrope', sans-serif;
        overflow-x: hidden;
    }

    .app-layout {
        display: flex;
        min-height: 100vh;
        padding-top: 72px; 
    }

    .main-content {
        flex: 1;
        margin-left: 256px; 
        position: relative;
    }

    @media (max-width: 768px) {
        .main-content {
            margin-left: 0;
        }
    }
</style>