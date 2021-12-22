<script>
    import InfoBoxItem from "$lib/components/InfoBoxItem.svelte";
    import FriendBlock from "$lib/components/FriendBlock.svelte";
    import photos from "$lib/data/photos.json";
    import topFriends from "$lib/data/friendsTop.json";
    import allFriends from "$lib/data/friendsAll.json";
    import CommentBox from "$lib/components/CommentBox.svelte";

    let friendsPlusOne = [...topFriends, {"name": "PhucdatRaiden", "image": "friend-raiden.jpg", "color": "#69c77a"}]

    let name = "Coco 💜 M.Y.";

    let birthday = "08-17-1991"
    let currentDate = new Date();
    let birthdayDate = new Date(birthday);
    let age = Math.floor((currentDate - birthdayDate) / 1000 / 60 /60 / 24 / 365);

    let formattedDate = currentDate;
    formattedDate = formattedDate.toString();
    formattedDate = formattedDate.split(" ");
    formattedDate = formattedDate[1] + " " + formattedDate[2] + ", " + formattedDate[3]

    let commentScrollHeight = 0;

    let pagination = 1;
    let paginationEnd = Math.ceil(photos.length / 10);
    let paginatedPhotosStart = 1;
    let paginatedPhotosEnd = 10;
    let paginatedPhotosCounter = 10;
    let parsedPhotos = photos.slice(paginatedPhotosStart - 1, paginatedPhotosStart - 1 + paginatedPhotosCounter);

    function calculatePhotoMaxPagination() {
        paginatedPhotosEnd = paginatedPhotosStart - 1 + paginatedPhotosCounter < photos.length
            ? paginatedPhotosStart - 1 + paginatedPhotosCounter
            : photos.length;
    }

    function handlePaginationPrev() {
        pagination--;
        paginatedPhotosStart = paginatedPhotosStart - paginatedPhotosCounter;
        refreshParsedPhotos();
        calculatePhotoMaxPagination();
    }

    function handlePaginationNext() {
        pagination++;
        paginatedPhotosStart = paginatedPhotosStart + paginatedPhotosCounter;
        refreshParsedPhotos();
        calculatePhotoMaxPagination();
    }

    function refreshParsedPhotos() {
        parsedPhotos = photos.slice(paginatedPhotosStart - 1, paginatedPhotosStart - 1 + paginatedPhotosCounter);
        parsedPhotos = [...parsedPhotos];

        handleCommentScroll();
    }

    function handleCommentScroll() {
        let lol = document.getElementById("comments-section")
        console.log(">>>lol.offsetHeight", lol.offsetTop)
        commentScrollHeight = lol.offsetTop
    }
</script>


<svelte:window bind:scrollY={commentScrollHeight}/>


<div class="row">
    <aside class="col-xl-5">
        <div class="homepage-profile border-thick bg-white">
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

        <div class="song-embed border-thick mb-4">
            <iframe width="100%" height="150" class="d-block m-0 p-0" src="https://www.youtube-nocookie.com/embed/qGjAWJ2zWWI" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
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

        <div class="bg-white shadow-lg mb-4 pb-3">
            <h3 class="header-green">{name}'s Blurbs:</h3>
            <div class="padding-content-small">
                <h4 class="subheader-green">About me:</h4>
                <p>I love Min Yoongi.</p>
            </div><!-- end small padding -->
        </div><!-- end spacer -->

        <div class="bg-white shadow-lg mb-5">
            <h3 class="header-green">{name}'s Friend Space</h3>

            <div class="padding-content-small">
                <h4 class="subheader-green mb-5">{name} has 613 Friends</h4>

                <div class="row">
                    {#each friendsPlusOne as friend}
                        <FriendBlock name={friend.name} src={friend.image} color={friend.color} />
                    {/each}
                </div><!-- end row -->

                <p class="text-end">
                    <!--<a href="https://www.google.com/search?as_st=y&tbm=isch&as_q=yoongi&as_epq=&as_oq=&as_eq=&imgsz=&imgar=&imgc=&imgcolor=&imgtype=&cr=&as_sitesearch=&safe=images&as_filetype=&tbs=" target="_blank" rel="noreferrer">View more of {name}'s Friends</a>-->

                    <button type="button"
                            class="btn btn-link px-4"
                            data-bs-toggle="modal"
                            data-bs-target="#moreFriendsModal">View more of {name}'s Friends</button>
                </p>


            </div><!-- end small padding -->
        </div><!-- end spacer -->

        <div id="comments-section" class="bg-white shadow-lg mb-4">
            <h3 class="header-green">{name}'s Comments:</h3>
            <div class="padding-content-small">
                <div class="d-flex align-items-center justify-content-between mb-2">
                    <h4 class="subheader-green">
                        Listing
                        {paginatedPhotosStart} - {paginatedPhotosEnd}
                        out of
                        {photos.length}
                        comments
                    </h4>

                    <button class="btn btn-light btn-sm fw-bold ms-auto me-2"
                            on:click={handlePaginationPrev} disabled={pagination <= 1}>Previous</button>

                    <button class="btn btn-light btn-sm fw-bold"
                            on:click={handlePaginationNext} disabled={pagination >= paginationEnd}>Next</button>
                </div><!-- end flexbox -->


                {#key pagination}
                    {#each parsedPhotos as photo, index}
                        <CommentBox src={photo} counter={index + (paginatedPhotosCounter * (pagination - 1))} />
                    {/each}
                {/key}


                <div class="text-end py-4">
                    <button class="btn btn-light btn-sm fw-bold ms-auto me-2"
                            on:click={handlePaginationPrev} disabled={pagination <= 1}>Previous</button>

                    <button class="btn btn-light btn-sm fw-bold"
                            on:click={handlePaginationNext} disabled={pagination >= paginationEnd}>Next</button>
                </div>
            </div><!-- end small padding -->
        </div><!-- end spacer -->
    </section><!-- end col -->
</div><!-- end row -->



<div class="modal fade" id="moreFriendsModal" tabindex="-1" aria-labelledby="moreFriendsModalLabel" aria-hidden="true">
    <div class="modal-dialog modal-dialog-centered modal-lg">
        <div class="modal-content">
            <div class="modal-header border-0">
                <h5 class="modal-title" id="moreFriendsModalLabel">{name}'s Friends</h5>
                <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
            </div>
            <div class="modal-body">
                <div class="row">
                    {#each allFriends as friend}
                        <FriendBlock name={friend.name} src={friend.image} color={friend.color} allFriendsList={true} />
                    {/each}
                </div>
            </div>
            <div class="modal-footer border-0">
                <button type="button" class="btn btn-secondary px-5" data-bs-dismiss="modal">Close 💜</button>
            </div>
        </div>
    </div>
</div>




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

    .info-box {
        background-color: #fff;
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