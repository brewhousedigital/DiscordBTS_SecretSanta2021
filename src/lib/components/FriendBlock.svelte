<script>
    export let name = "";
    export let src = "";
    export let columns = true;
</script>


<div class="{columns ? 'col-md-3 col-6' : ''} text-center mb-5">
    <p class="mb-1 fw-bold">{name}</p>
    <img src={"/images/" + src} alt="Profile pic for {name}" class="img-fluid d-block">
</div>


<style>
    img {
        border: 2px solid #8fd8be;
    }
</style>