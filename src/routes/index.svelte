<script>
    import InfoBoxItem from "$lib/components/InfoBoxItem.svelte";
    import FriendBlock from "$lib/components/FriendBlock.svelte";
    import photos from "$lib/data/photos.json";
    import friends from "$lib/data/friends.json";
    import CommentBox from "$lib/components/CommentBox.svelte";

    let friendsPlusOne = [...friends, {"name": "Raiden", "image": "friend-raiden.jpg"}]

    let name = "Coco 💜 M.Y.";

    let birthday = "08-17-1991"
    let currentDate = new Date();
    let birthdayDate = new Date(birthday);
    let age = Math.floor((currentDate - birthdayDate) / 1000 / 60 /60 / 24 / 365);
    let formattedDate = currentDate.toString().split(" ");
    formattedDate = formattedDate[1] + " " + formattedDate[2] + ", " + formattedDate[3]


</script>


<div class="row">
    <aside class="col-xl-5">
        <div class="homepage-profile bg-white">
        <h2 class="mb-4">{name}</h2>

        <div class="row align-items-center">
            <div class="col-4">
                <img src="/images/profile-pic.jpg" alt="Coco's profile photo of Suga" class="img-fluid">
            </div><!-- end col -->

            <div class="col-8">
                <p class="mb-0">{age} years old</p>
                <p class="mb-3">Vancouver, British Colombia <br>Canada</p>

                <p class="online-now mb-3 fw-bold"><i class="bi bi-person-fill"></i> Online Now!</p>

                <p class="mb-0">Last Login: {formattedDate}</p>
            </div><!-- end col -->
        </div><!-- end row -->
        </div>

        <div class="arrspace-url border-thick mb-4 bg-white">
            <p class="fw-bolder mb-0">MySpace URL:</p>
            <p class="mb-0">https://iloveminyoongi613.netlify.app</p>
        </div>

        <div class="song-embed mb-4">
            <iframe width="100%" height="150" src="https://www.youtube-nocookie.com/embed/qGjAWJ2zWWI" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
        </div><!-- song embed -->

        <div class="info-box border-thick mb-4">
            <h3>{name}'s Interests</h3>

            <div class="info-box-content">
                <InfoBoxItem title="General" content="Men who look like they could kill you but are actually a cinnamon roll" />
                <InfoBoxItem title="Music" content="BTS, Agust D, Suga" />
                <InfoBoxItem title="Books" content="Pure, White, and Deadly: How Suga Is Killing Us and What We Can Do to Stop It by John Yudkin;" />
                <InfoBoxItem title="Heroes" content="Min Yoongi" />
            </div><!-- end info content -->
        </div><!-- end info box -->

        <div class="info-box border-thick mb-5">
            <h3>{name}'s Details</h3>

            <div class="info-box-content">
                <InfoBoxItem title="Status" content="Married to Yoongi" />
                <InfoBoxItem title="Here for" content="hands, white tees, tongues" />
                <InfoBoxItem title="Hometown" content="Daegu (I wish!)" />
                <InfoBoxItem title="Zodiac" content="Leo" />
                <InfoBoxItem title="Occupation" content="Professional Violence Bringer" />
            </div><!-- end info content -->
        </div><!-- end info box -->
    </aside><!-- end col -->

    <section class="col-xl-7">
        <img src="/images/banner-2.jpg" class="img-fluid mb-4 d-block" alt="banner for Suga">

        <div class="bg-white mb-4 pb-3">
            <h3 class="header-green">{name}'s Blurbs:</h3>
            <div class="padding-content-small">
                <h4 class="subheader-green">About me:</h4>
                <p>I love Min Yoongi.</p>
            </div><!-- end small padding -->
        </div><!-- end spacer -->

        <div class="bg-white mb-5">
            <h3 class="header-green">{name}'s Friend Space</h3>

            <div class="padding-content-small">
                <h4 class="subheader-green mb-5">{name} has 613 Friends</h4>

                <div class="row">
                    {#each friendsPlusOne as friend}
                        <FriendBlock name={friend.name} src={friend.image} />
                    {/each}
                </div><!-- end row -->

                <p class="text-end"><a href="https://www.google.com/search?as_st=y&tbm=isch&as_q=yoongi&as_epq=&as_oq=&as_eq=&imgsz=&imgar=&imgc=&imgcolor=&imgtype=&cr=&as_sitesearch=&safe=images&as_filetype=&tbs=" target="_blank" rel="noreferrer">View all of {name}'s Friends</a></p>
            </div><!-- end small padding -->
        </div><!-- end spacer -->

        <div class="bg-white mb-4">
            <h3 class="header-green">{name}'s Comments:</h3>
            <div class="padding-content-small">
                <h4 class="subheader-green">Listing all {photos.length} comments</h4>

                {#each photos as photo, index}
                    <CommentBox src={photo} counter={index} />
                {/each}
            </div><!-- end small padding -->
        </div><!-- end spacer -->
    </section><!-- end col -->
</div><!-- end row -->


<style>
    .online-now {
        color: #8fd8be;
    }

    .arrspace-url {
        padding: 8px;
    }

    .song-embed {

    }

    .border-thick {
        border: 2px solid black;
    }

    .info-box h3 {
        font-size: 16px;
        font-weight: 700;
        background-color: #8fd8be;
        padding: 4px 8px;
        margin-bottom: 0;
        border-bottom: 2px solid black;
    }

    .info-box-content {
        background-color: #fff;
        padding: 4px 4px 0 4px;
    }

    .header-green {
        background-color: #8fd8be;
        color: #fff;
        padding: 4px 8px;
        font-size: 16px;
    }

    .subheader-green {
        color: #8fd8be;
        font-size: 16px;
    }

    .padding-content-small {
        padding-left: 8px;
        padding-right: 8px;
    }

    .homepage-profile {
        padding: 16px;
        margin-bottom: 24px;
    }
    .bg-white {
        background-color: rgba(255, 255, 255, 0.9);
    }
</style>