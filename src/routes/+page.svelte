<script lang="ts">
    import markdownit from 'markdown-it';
    import mdtcapimg from '@maksiks/markdown-it-image-caption'

    const md = $state(markdownit()
        .use(mdtcapimg));

    let textBoxContent = $state('hi');
    const text = $derived(md.render(textBoxContent));
</script>

<main>
    <section class="edit">
        <p>✏️ Write something in here</p><br>
        <!-- Can't do it in Markdown because of my own plugin, funniest thing ever -->
        <p class="small"> For example: <br> <code>![test](https://i.pinimg.com/originals/0b/12/8a/0b128adee2c032cd1ab8d7d970917361.gif
            'Rendered 🎉!')</code></p>
        <textarea bind:value={textBoxContent}></textarea>
    </section>
    <section class="markdown">
        <p>{@html text}</p>
    </section>
</main>

<style>
    :global {
        body {
            background-color: #ffd58c;
            overflow-x: clip;
            overflow-y: auto;
        }

        * {
            margin: 0;
            padding: 0;

            font-family: Comfortaa, sans-serif;
        }
    }

    main {
        width: 100vw;
        height: 100vh;

        display: flex;
        flex-direction: column;
        align-items: center;

        & .edit {
            margin-top: 100px;
            display: flex;
            flex-direction: column;
            width: 40vw;

            & p {
                font-weight: bold;
                font-size: 1.2rem;
            }

            & .small {
                font-size: 0.8rem;
                color: black;
                background: #ceffa5;
                width: 100%;
                border-radius: 4px;
                padding: 6px 0 6px 6px;

            }

            & textarea {
                margin-top: 10px;

                width: 100%;
                height: 20vh;
            }
        }

        & .markdown {
            width: 60%;

            & p {
                margin-top: 50px;
                font-weight: bold;
                font-size: 1rem;


                padding-bottom: 50px;

                :global {
                    figure {
                        & img {
                            max-width: 100%;
                        }
                    }
                }
            }
        }

    }
</style>