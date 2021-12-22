<script>
    import friends from "$lib/data/friendsAll.json";
    import Photo from "$lib/components/Photo.svelte";
    import FriendBlock from "$lib/components/FriendBlock.svelte";

    export let src = "";
    export let counter = 0;

    let currentDate = new Date();
    let newDate = currentDate.setDate(currentDate.getDate() - counter);
    let formattedDate = new Date(newDate);
    formattedDate = formattedDate.toString();
    formattedDate = formattedDate.split(" ");
    formattedDate = formattedDate[1] + " " + formattedDate[2] + ", " + formattedDate[3]

    const randomFriend = friends[Math.floor(Math.random() * friends.length)];
</script>


<div class="row">
    <div class="col-4">
        <div class="title h-100 px-lg-5 px-3 pt-3">
            <FriendBlock columns={false} name={randomFriend.name} color={randomFriend.color} src={randomFriend.image} />
        </div>
    </div><!-- end col -->

    <div class="col-8">
        <div class="content h-100">
            <p class="small fw-bold mb-2">{formattedDate}</p>
            <Photo src="/images/photos/{src}" />
        </div>
    </div><!-- end col -->
</div><!-- end row -->


<style>
    .title {
        background-color: #8fd8be99;
        padding: 4px;
    }

    .content {
        background-color: #8fd8be50;
        padding: 4px;
    }

    .row {
        margin-bottom: 4px;
    }

    .col-4 {
        padding: 0 2px 0 12px;
    }

    .col-8 {
        padding: 0 12px 0 2px;
    }
</style>