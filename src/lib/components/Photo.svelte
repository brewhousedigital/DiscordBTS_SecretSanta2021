<script>
    export let src = "";
    export let alt = "";
    export let classes = "";

    let fileType = src.split(".");
    fileType = fileType[fileType.length - 1];
    fileType = fileType.toLowerCase();
</script>


{#if fileType === "mp4"}
    <video width="100%" class="{classes}" loop autoplay muted>
        <source src="{src}" type="video/mp4" aria-label={alt}>
        Your browser does not support the video tag.
    </video>
{:else}
    <img src="{src}" alt={alt} class="img-fluid {classes}" loading="lazy">
{/if}


<style>
    video, img {
        display: block;
        margin-bottom: 10px;
    }
</style>