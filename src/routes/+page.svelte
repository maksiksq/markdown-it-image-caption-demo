<script lang="ts">
    import markdownit from 'markdown-it';
    import mdtcapimg from '@maksiks/markdown-it-image-caption'

    const md = $state(markdownit()
        .use(mdtcapimg));

    let textBoxContent = $state('hi');
    const text = $derived(md.render(textBoxContent));
</script>

<main>
    <section>
        <p>✏️ write something in here</p>
        <textarea bind:value={textBoxContent}></textarea>

        <p>{@html text}</p>
    </section>
</main>

<style>
    :global {
        body {
            background-color: #ffd58c;
            overflow: clip;
        }

        * {
            margin: 0;
            padding: 0;
        }
    }

    main {
        width: 100vw;
        height: 100vh;

        display: flex;
        justify-content: center;
        align-items: center;

        section {
            display: flex;
            flex-direction: column;

            p {
                font-weight: bold;
                font-size: 1.2rem;
                font-family: Comfortaa, sans-serif;
            }

            textarea {
                margin-top: 10px;

                width: 40vw;
                height: 50vh;
            }
        }
    }
</style>