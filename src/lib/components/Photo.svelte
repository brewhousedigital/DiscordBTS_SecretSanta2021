<script>
    export let src = "";

    let fileType = src.split(".");
    fileType = fileType[fileType.length - 1];
    fileType = fileType.toLowerCase();
</script>


{#if fileType === "mp4"}
    <video width="100%" loop autoplay muted controls>
        <source src="/images/photos/{src}" type="video/mp4">
        Your browser does not support the video tag.
    </video>
{:else}
    <img src="/images/photos/{src}" alt="" class="img-fluid" loading="lazy">
{/if}


<style>
    video, img {
        display: block;
        margin-bottom: 10px;
    }
</style>