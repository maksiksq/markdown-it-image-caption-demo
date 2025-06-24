<script lang="ts">
    import markdownit from 'markdown-it';
    import mdtcapimg from '@maksiks/markdown-it-image-caption'

    const md = $state(markdownit()
        .use(mdtcapimg, {
            allImgClasslist: '.fig',
        }));

    let textBoxContent = $state('hi i\'m writable');
    const text = $derived(md.render(textBoxContent));
</script>

<svelte:head>
    <title>Example</title>
</svelte:head>

<div class="githubFloatie">
    <a title="GitHub repository" href="https://github.com/maksiksq/markdown-it-image-caption-demo" target="_blank"
       rel="noopener noreferrer">
        <img src="/img/gitlogo.svg" alt="Github page link">
    </a>
</div>
<main>
    <section class="edit">
        <p class="head">✏️ Write something in here</p><br>
        <!-- Can't do it in Markdown because of my own plugin, funniest thing ever  -->
        <p class="small"> Try: <br> <code>![test](https://i.pinimg.com/originals/0b/12/8a/0b128adee2c032cd1ab8d7d970917361.gif 'Rendered 🎉!')</code></p>
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

    .githubFloatie {
        position: absolute;
        top: 30px;
        right: 30px;

        & a {
            & img {
                width: 2.1rem;
            }
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
            width: 90%;

            & .head {
                padding-bottom: 8px;
                border-bottom: 1px #353535 solid;
            }

            & p {
                font-weight: bold;
                font-size: 1.2rem;
            }

            & .small {
                box-sizing: border-box;
                font-size: 0.8rem;
                color: black;
                background: #ceffa5;
                width: 100%;
                border-radius: 4px;
                padding: 6px 0 6px 6px;
                border: 1px solid #616161;

                code {
                    width: 100%;
                    white-space: pre-wrap;
                    word-break: break-word;
                }
            }

            & textarea {
                box-sizing: border-box;
                margin-top: 10px;
                border-radius: 4px;
                padding: 6px 6px 6px 6px;

                width: 100%;
                height: 20vh;
            }
        }

        & .markdown {
            width: 90%;
            white-space: pre-wrap;
            word-break: break-word;

            & p {
                margin-top: 50px;
                font-weight: bold;
                font-size: 1rem;

                border-radius: 4px;
                background-color: #ffffff;
                border: 1px #353535 solid;

                padding: 16px 16px 50vh 16px;

                & img {
                    max-width: 100%;
                }

                :global {
                    .fig {
                        & img {
                            max-width: 100%;
                        }
                    }
                }
            }
        }

    }
</style>