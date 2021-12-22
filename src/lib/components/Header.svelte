<script>
    import photos from "$lib/data/photos.json";
    import shuffleArray from "$lib/functions/shuffleArray";
    import Photo from "$lib/components/Photo.svelte";

    let validSearchOptions = [
        "min yoongi", "minyoongi", "suga", "agust d", "agustd", "yoongi", "lil meow", "lil meow meow", "min pd", "minpd", "yoonji",
    ]

    let searchValue = "";
    let searchError = false;
    let searchResults = [];

    function handleSearch(e) {
        e.preventDefault();
        searchResults = [];

        // Copy the JSON list
        let temporaryArray = [...photos];

        // Randomize the list
        shuffleArray(temporaryArray)

        // Grab ten
        searchResults = temporaryArray.slice(0, 10);
        searchResults = [...searchResults];

        let formattedSearchValue = searchValue.toLowerCase();
        let modalElement = document.getElementById('searchModal');

        validSearchOptions.includes(formattedSearchValue) ? searchError = false : searchError = true;

        let modal = new bootstrap.Modal(modalElement);
        modal.show();
    }
</script>


<div class="container">
    <header class="row align-items-center py-4 pe-3">
        <div class="col-xl-5">
            <div class="d-flex align-items-center">
                <img src="/images/logo-white-sm.png" alt="BTS logo" id="header-logo-image" class="img-fluid">
                <h1>myspace</h1>
            </div>
        </div><!-- end col -->

        <div class="col-xl-7">
            <form id="header-search-bar" on:submit={handleSearch} class="d-flex">
                <input type="text"
                       class="form-control me-2"
                       bind:value={searchValue}
                       aria-label="Search"
                       name="search"
                       aria-describedby="search-button">
                <button class="btn btn-light" type="submit" id="search-button">Search</button>
            </form>
        </div><!-- end col -->
    </header>
</div>


<div class="modal fade" id="searchModal" tabindex="-1" aria-labelledby="searchModalLabel" aria-hidden="true">
    <div class="modal-dialog modal-dialog-centered modal-lg">
        <div class="modal-content">
            <div class="modal-header border-0">
                <h5 class="modal-title" id="searchModalLabel">Search Results</h5>
                <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
            </div>
            <div class="modal-body">
                {#if searchError}
                    <div class="alert alert-warning fw-bold" role="alert">Something must have gone wrong. We were expecting you to search for "Yoongi" but you searched something else? How strange. Here are some images of Yoongi for you anyways.</div>
                {/if}

                <div class="masonry-grid">
                {#each searchResults as photo}
                    <Photo src="/images/photos/{photo}" />
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
    header {
        background-color: #1b5cb9;
        color: #fff;
    }

    #header-logo-image {
        max-width: 50px;
    }

    .masonry-grid {
        column-count: 4;
        column-gap: 10px;
    }
</style>