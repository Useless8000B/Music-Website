<script lang="ts">
  import { page } from "$app/stores";

  let { activeRoute = "/", isOpen = false } = $props();

  interface MenuItem {
    icon: string;
    label: string;
    path: string;
  }

  const menuItems: MenuItem[] = [
    { icon: "home", label: "Home", path: "/" },
    { icon: "bolt", label: "Trending", path: "/#trending-now" },
    { icon: "radio", label: "Radio", path: "/radio" },
    { icon: "grid_view", label: "Genres", path: "/genres" },
    { icon: "new_releases", label: "New Releases", path: "/new-releases" },
  ];

  const isActive = (path: string) => {
    if (path === "/") return $page.url.pathname === "/" && !$page.url.hash;
    if (path.includes("#")) return $page.url.hash === "#trending-now";
    return $page.url.pathname === path;
  };
</script>

<aside class="sidebar" class:is-open={isOpen}>
  <div class="sidebar-header">
    <div class="header-content">
        <h3 class="brand-title">The Sonic Editorial</h3>
        <p class="brand-subtitle">Premium Sound</p>
    </div>
  </div>

  <nav class="nav-menu">
    {#each menuItems as item}
      <a href={item.path} class="nav-link" class:active={isActive(item.path)}>
        <span class="material-symbols-outlined">{item.icon}</span>
        <span class="link-text">{item.label}</span>
      </a>
    {/each}
  </nav>

  <div class="sidebar-footer">
    <div class="status-indicator">
        <span class="dot"></span>
        <span class="status-text">System Online</span>
    </div>
  </div>
</aside>

<style lang="scss">
  .sidebar {
    height: 100vh;
    width: 280px;
    background-color: #0e0e13;
    display: flex;
    flex-direction: column;
    position: fixed;
    top: 0;
    left: 0;
    z-index: 100;

    transform: translateX(-100%);
    transition: transform 0.4s cubic-bezier(0.16, 1, 0.3, 1);

    &.is-open {
      transform: translateX(0);
      box-shadow: 20px 0 60px rgba(0, 0, 0, 0.8);
    }

    @media (min-width: 1024px) {
      transform: translateX(0);
      width: 256px;
      z-index: 30;
    }

    .sidebar-header {
      padding: 2rem 1.5rem;
      margin-bottom: 1rem;

      .brand-title {
        font-family: "Space Grotesk", sans-serif;
        font-size: 1.1rem;
        font-weight: 900;
        color: #81ecff;
        line-height: 1.2;
      }

      .brand-subtitle {
        font-size: 0.6rem;
        text-transform: uppercase;
        letter-spacing: 0.15em;
        color: #64748b;
        font-weight: 700;
      }
    }

    .nav-menu {
      display: flex;
      flex-direction: column;
      gap: 0.5rem;
      padding: 0 1rem;

      .nav-link {
        display: flex;
        align-items: center;
        gap: 1rem;
        padding: 0.85rem 1.25rem;
        text-decoration: none;
        color: #64748b;
        font-family: "Space Grotesk", sans-serif;
        font-weight: 700;
        border-radius: 12px;
        transition: all 0.3s ease;

        .material-symbols-outlined {
            font-size: 1.4rem;
        }

        &:hover {
          background-color: rgba(255, 255, 255, 0.03);
          color: #81ecff;
        }

        &.active {
          color: #81ecff;
          background-color: rgba(129, 236, 255, 0.1);
        }
      }
    }

    .sidebar-footer {
        margin-top: auto;
        padding: 2rem 1.5rem;
        
        .status-indicator {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            font-size: 0.65rem;
            color: #475569;
            text-transform: uppercase;
            font-weight: 800;

            .dot {
                width: 6px;
                height: 6px;
                background-color: #10b981;
                border-radius: 50%;
                box-shadow: 0 0 8px #10b981;
            }
        }
    }
  }
</style>