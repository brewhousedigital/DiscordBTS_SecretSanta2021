<script>
    import Header from "$lib/components/Header.svelte";
    import fairyDustCursor from "$lib/functions/cursorFairyDust";
    import {onMount} from "svelte";

    onMount(() => {
        fairyDustCursor();
    })

    function handleBackgroundSwitch() {
        document.body.classList.toggle("different-bg")
    }
</script>


<div class="container">
    <button class="btn background-switcher"
            type="button" on:click={handleBackgroundSwitch}>🌟</button>

    <Header />

    <main>
        <slot></slot>
    </main>
</div>


<style>
    :global(body) {
        background-image: url("/images/background-2.jpg");
        background-position: center;
        background-attachment: fixed;
        font-family: cursive;
    }

    :global(body.different-bg) {
        background-image: url("/images/background.jpg");
    }

    main {
        padding: 24px;
        /*background-color: rgba(255, 255, 255, 0.9);*/
    }

    .background-switcher {
        position: absolute;
        top: 8px;
        right: 8px;
    }
</style>