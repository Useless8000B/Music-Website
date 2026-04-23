<section class="hero">
  <div class="background-wrap">
    <img
      src="https://images.unsplash.com/photo-1614613535308-eb5fbd3d2c17?q=80&w=2070&auto=format&fit=crop"
      alt="Featured Artist"
    />
    <div class="gradient-overlay horizontal"></div>
    <div class="gradient-overlay vertical"></div>
  </div>

  <div class="content">
    <span class="badge">Artist of the month</span>

    <h1>
      KAIROS <br />
      <span class="accent">STORM</span>
    </h1>

    <p>
      Experience the visceral energy of 'Midnight Echoes' — the chart-topping
      album that redefines cinematic synth-pop.
    </p>

    <div class="actions">
      <button class="btn-primary">
        <span class="material-symbols-outlined">play_arrow</span>
        PLAY LATEST ALBUM
      </button>
      <button class="btn-outline"> FOLLOW ARTIST </button>
    </div>
  </div>
</section>

<style lang="scss">
  .hero {
    position: relative;
    min-height: 70vh;
    display: flex;
    align-items: center;
    padding: 2rem;
    overflow: hidden;
    border-radius: 1.5rem;
    margin: 0.5rem;

    @media (min-width: 1024px) {
      padding: 0 4rem;
      border-radius: 2rem;
      margin: 1rem;
    }

    .background-wrap {
      position: absolute;
      inset: 0;
      z-index: 0;

      img {
        width: 100%;
        height: 100%;
        object-fit: cover;
        opacity: 0.6;
      }

      .gradient-overlay {
        position: absolute;
        inset: 0;

        &.horizontal {
          background: linear-gradient(
            to right,
            #0e0e13 10%,
            rgba(14, 14, 19, 0.4) 50%,
            transparent 100%
          );

          @media (min-width: 1024px) {
            background: linear-gradient(
              to right,
              #0e0e13 10%,
              rgba(14, 14, 19, 0.4) 50%,
              transparent 100%
            );
          }
        }

        &.vertical {
          background: linear-gradient(to top, #0e0e13 40%, transparent 90%);
        }
      }
    }

    .content {
      position: relative;
      z-index: 10;
      max-width: 600px;

      @media (min-width: 1024px) {
        margin-top: 0;
      }

      .badge {
        background: #ff51fa;
        color: #400040;
        padding: 0.25rem 0.75rem;
        border-radius: 99px;
        font-size: 0.65rem;
        font-weight: 900;
        text-transform: uppercase;
        letter-spacing: 0.1em;
        display: inline-block;
        margin-bottom: 1.5rem;
      }

      h1 {
        font-family: "Space Grotesk", sans-serif;
        font-size: clamp(2.5rem, 10vw, 6rem);
        font-weight: 900;
        line-height: 1;
        letter-spacing: -0.04em;
        margin-bottom: 1rem;

        .accent {
          color: #81ecff;
          font-style: italic;
        }
      }

      p {
        font-size: 1rem;
        color: #cbd5e1;
        font-weight: 300;
        line-height: 1.6;
        margin-bottom: 2rem;

        @media (min-width: 1024px) {
          font-size: 1.25rem;
        }
      }

      .actions {
        display: flex;
        flex-direction: column;
        gap: 1rem;

        @media (min-width: 640px) {
          flex-direction: row;
        }

        button {
          padding: 1rem 1.5rem;
          border-radius: 99px;
          font-weight: bold;
          width: 100%;
          justify-content: center;
          font-family: "Space Grotesk", sans-serif;
          cursor: pointer;
          transition:
            transform 0.2s,
            box-shadow 0.2s;

          @media (min-width: 640px) {
            width: auto;
          }

          &.btn-primary {
            background: #00e3fd;
            color: #003840;
            border: none;
            display: flex;
            align-items: center;
            gap: 0.5rem;
            box-shadow: 0 0 20px rgba(129, 236, 255, 0.2);

            &:hover {
              transform: scale(1.05);
              box-shadow: 0 0 30px rgba(129, 236, 255, 0.4);
            }
          }

          &.btn-outline {
            background: transparent;
            color: #f9f5fd;
            border: 1px solid rgba(255, 255, 255, 0.2);

            &:hover {
              background: rgba(255, 255, 255, 0.05);
            }
          }
        }
      }
    }
  }
</style>
