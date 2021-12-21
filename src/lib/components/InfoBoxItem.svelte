<script>
    export let title = "";
    export let content = "";
</script>


<div class="row">
    <div class="col-md-5 fw-bold">
        <div class="title h-100">{title}</div>
    </div><!-- end col -->

    <div class="col-md-7">
        <div class="content h-100">{content}</div>
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

    .col-md-5 {
        padding: 0 2px 0 12px;
    }

    .col-md-7 {
        padding: 0 12px 0 2px;
    }
</style>