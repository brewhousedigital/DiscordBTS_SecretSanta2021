<script>
    export let handlePaginationPrev;
    export let handlePaginationNext;
    export let pagination;
    export let paginationEnd;
</script>


<button class="btn btn-light btn-sm fw-bold ms-auto me-2"
        on:click={handlePaginationPrev} disabled={pagination <= 1}>Previous</button>

<button class="btn btn-light btn-sm fw-bold"
        on:click={handlePaginationNext} disabled={pagination >= paginationEnd}>Next</button>