<script>
    import Photo from "$lib/components/Photo.svelte";

    export let name = "";
    export let src = "";
    export let color = "#222";
    export let columns = true;
    export let allFriendsList = false;
</script>


<div class="{columns ? 'col-md-3 col-6' : ''} text-center mb-5">
    <p class="mb-1 bg-dark"
       style="color: {color}; {allFriendsList && 'display:flex;align-items:center;justify-content:center;height:48px'}">{name}</p>
    <Photo src={"/images/friends/" + src} alt="Profile pic for {name}" classes="img-fluid d-block" />
</div>


<style>
    img {
        border: 2px solid #8fd8be;
    }
</style>