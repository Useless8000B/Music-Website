<script>
  let { activeRoute = '/' } = $props();

  const menuItems = [
    { icon: 'home', label: 'Home', path: '/' },
    { icon: 'bolt', label: 'Trending', path: '/trending' },
    { icon: 'radio', label: 'Radio', path: '/radio' },
    { icon: 'grid_view', label: 'Genres', path: '/genres' },
    { icon: 'new_releases', label: 'New Releases', path: '/new-releases' }
  ];
</script>

<aside class="sidebar">
  <div class="sidebar-header">
    <h3 class="brand-title">The Sonic Editorial</h3>
    <p class="brand-subtitle">Premium Sound</p>
  </div>

  <nav class="nav-menu">
    {#each menuItems as item}
      <a href={item.path} class="nav-link" class:active={activeRoute === item.path}>
        <span class="material-symbols-outlined">{item.icon}</span>
        <span class="link-text">{item.label}</span>
      </a>
    {/each}
  </nav>
</aside>

<style lang="scss">
  .sidebar {
    height: 100%;
    width: 256px;
    background-color: #0e0e13;
    display: flex;
    flex-direction: column;
    position: fixed;
    z-index: 30;

    .sidebar-header {
      padding: 0 1.5rem;
      margin-bottom: 2rem;

      .brand-title {
        font-family: 'Space Grotesk', sans-serif;
        font-size: 1.25rem;
        font-weight: 900;
        color: #81ecff;
      }

      .brand-subtitle {
        font-size: 0.65rem;
        text-transform: uppercase;
        letter-spacing: 0.15em;
        color: #64748b;
        font-weight: 700;
      }
    }

    .nav-menu {
      display: flex;
      flex-direction: column;
      gap: 0.25rem;

      .nav-link {
        display: flex;
        align-items: center;
        gap: 1rem;
        padding: 0.75rem 1rem;
        text-decoration: none;
        color: #64748b;
        font-family: 'Space Grotesk', sans-serif;
        font-weight: 700;
        transition: all 0.3s ease;

        &:hover {
          background-color: #131319;
          color: #81ecff;
        }

        &.active {
          color: #81ecff;
          background-color: #131319;
          border-radius: 0 9999px 9999px 0;
          margin-right: 1rem;
        }
      }
    }
  }
</style>