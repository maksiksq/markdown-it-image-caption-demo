<main>
    <section>
        <p>write something in here</p>
        <textarea></textarea>
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
                width: 100%;
            }
        }
    }
</style>