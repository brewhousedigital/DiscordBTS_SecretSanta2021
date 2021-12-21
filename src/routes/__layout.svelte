<script>
    import Header from "$lib/components/Header.svelte";
    import fairyDustCursor from "$lib/functions/cursorFairyDust";
    import {onMount} from "svelte";

    onMount(() => {
        fairyDustCursor();
    })
</script>


<div class="container">
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
    main {
        padding: 24px;
        /*background-color: rgba(255, 255, 255, 0.9);*/
    }
</style>