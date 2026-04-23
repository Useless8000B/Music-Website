<script lang="ts">
    interface Props {
        title: string;
        artist: string;
        cover: string;
        date?: string;
        type: "single" | "album";
    }

    let { title, artist, cover, date, type }: Props = $props();
</script>

<div class="release-card {type}">
    <div class="image-container">
        <img src={cover} alt={title} loading="lazy" />
        <button class="play-overlay">
            <span class="material-symbols-outlined">play_arrow</span>
        </button>
    </div>
    <div class="metadata">
        <h4>{title}</h4>
        <p class="artist">{artist}</p>
        {#if date}
            <p class="date">{date}</p>
        {/if}
    </div>
</div>

<style lang="scss">
    .release-card {
        cursor: pointer;
        display: flex;
        flex-direction: column;
        align-items: flex-start;
        gap: 0.75rem;
        transition: transform 0.3s ease;

        .image-container {
            position: relative;
            flex-shrink: 0;
            overflow: hidden;
            background: #19191f;
            width: 100%;
            height: auto;
            border-radius: 1rem;

            img {
                width: 100%;
                height: 100%;
                object-fit: cover;
            }
        }

        &.single .image-container {
            aspect-ratio: 16 / 9;
        }

        &.album .image-container {
            aspect-ratio: 1 / 1;
        }

        .play-overlay {
            display: flex;
            position: absolute;
            bottom: 0.75rem;
            right: 0.75rem;
            background: #81ecff;
            color: #003840;
            border: none;
            padding: 0.5rem;
            border-radius: 50%;
            opacity: 0;
            transform: translateY(10px);
            transition: all 0.3s ease;
        }

        @media (hover: hover) {
            &:hover {
                .play-overlay {
                    opacity: 1;
                    transform: translateY(0);
                }
            }
        }

        .metadata {
            flex: 1;
            min-width: 0;
            width: 100%;

            h4 {
                font-size: 0.9rem;
                font-weight: 700;
                margin: 0;
                white-space: nowrap;
                overflow: hidden;
                text-overflow: ellipsis;
                color: #f9f5fd;
            }

            .artist {
                color: #acaab1;
                font-size: 0.8rem;
                margin: 0.1rem 0;
            }

            .date {
                font-size: 0.65rem;
                color: #76747b;
            }
        }
    }
</style>