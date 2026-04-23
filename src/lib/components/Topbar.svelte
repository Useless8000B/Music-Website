<script lang="ts">
  import { page } from "$app/stores";

  let { toggleSidebar } = $props();

  const isActive = (path: string) => {
    const currentPath = $page.url.pathname;
    if (path === "/") return currentPath === "/";
    return currentPath.startsWith(path);
  };
</script>

<nav class="topbar">
  <div class="left-section">
    <span class="logo">Sonic Pulse</span>

    <div class="nav-links">
      <a href="/" class:active={isActive("/")}>Explore</a>
      <a href="/library" class:active={isActive("/library")}>Library</a>
      <a href="/live" class:active={isActive("/live")}>Live</a>
    </div>
  </div>

  <div class="right-section">
    <div class="search-bar desktop-only">
      <span class="material-symbols-outlined">search</span>
      <input type="text" placeholder="Artists, songs, or podcasts" />
    </div>

    <div class="actions">
      <button class="icon-btn">
        <span class="material-symbols-outlined">notifications</span>
      </button>
      <button class="icon-btn">
        <span class="material-symbols-outlined">settings</span>
      </button>
      <div class="profile-pic">
        <img
          src="https://ui-avatars.com/api/?name=User&background=81ecff&color=004d57"
          alt="Profile"
        />
      </div>
      <!-- svelte-ignore a11y_consider_explicit_label -->
      <button
        class="mobile-menu mobile-only"
        onpointerdown={(e) => {
          toggleSidebar();
        }}
        aria-label="Open Menu"
      >
        <div class="line top"></div>
        <div class="line mid"></div>
        <div class="line bot"></div>
      </button>
    </div>
  </div>
</nav>

<style lang="scss">
  .topbar {
    position: fixed;
    width: 100%;
    top: 0;
    left: 0;
    height: 72px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0 1.5rem;
    background: rgba(14, 14, 19, 0.7);
    backdrop-filter: blur(20px);
    z-index: 90;

    @media (min-width: 1024px) {
      padding: 0 2rem;
    }

    .left-section {
      display: flex;
      align-items: center;
      gap: 3rem;

      .logo {
        font-family: "Space Grotesk", sans-serif;
        font-size: 1.5rem;
        font-weight: bold;
        color: #81ecff;
        letter-spacing: -1px;
      }

      .nav-links {
        display: none;
        gap: 2rem;

        @media (min-width: 1024px) {
          display: flex;
        }

        a {
          text-decoration: none;
          color: #94a3b8;
          font-family: "Space Grotesk", sans-serif;
          font-weight: 500;
          transition: color 0.2s;
          border-bottom: 2px solid transparent;
          padding-bottom: 4px;

          &:hover,
          &.active {
            color: #81ecff;
          }

          &.active {
            border-bottom: 2px solid #81ecff;
          }
        }
      }
    }

    .right-section {
      display: flex;
      align-items: center;
      gap: 1rem;

      @media (min-width: 1024px) {
        gap: 1.5rem;
      }

      .search-bar {
        display: none;

        @media (min-width: 1024px) {
          display: flex;
          align-items: center;
          background: rgba(37, 37, 45, 0.5);
          border: 1px solid rgba(255, 255, 255, 0.1);
          padding: 0.5rem 1rem;
          border-radius: 9999px;
          width: 300px;
        }

        span {
          font-size: 1.2rem;
          color: #acaab1;
          margin-right: 0.5rem;
        }

        input {
          background: transparent;
          border: none;
          outline: none;
          color: #f9f5fd;
          font-size: 0.85rem;
          width: 100%;
          &::placeholder {
            color: #64748b;
          }
        }
      }

      .actions {
        display: flex;
        align-items: center;
        gap: 0.75rem;

        @media (min-width: 1024px) {
          gap: 1rem;
        }

        .icon-btn {
          background: transparent;
          border: none;
          color: #94a3b8;
          cursor: pointer;
          display: flex;
          align-items: center;

          &.settings-btn {
            @media (max-width: 393px) {
              display: none;
            }
          }
        }

        .profile-pic {
          width: 32px;
          height: 32px;
          border-radius: 50%;
          overflow: hidden;
          border: 1px solid rgba(129, 236, 255, 0.3);
          img {
            width: 100%;
            height: 100%;
            object-fit: cover;
          }
        }

        .mobile-menu {
          display: flex;
          flex-direction: column;
          background: none;
          border: none;
          gap: 5px;
          padding: 8px;
          cursor: pointer;
          margin-left: 0.5rem;

          @media (min-width: 1024px) {
            display: none;
          }

          .line {
            background-color: #81ecff;
            width: 22px;
            height: 2px;
            border-radius: 99px;
            transition: all 0.3s ease;
          }

          .mid {
            width: 16px;
            align-self: flex-end;
          }

          &:active .line {
            background-color: white;
            transform: scaleX(1.1);
          }
        }
      }
    }
  }
</style>
