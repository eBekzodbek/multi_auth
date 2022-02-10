<template>
    <div>
        <form action="">
            <div class="row">
                <div class="col-md-8 m-lg-auto mb-4 mb-md-0">
                    <div class="input-group input-group-lg">
                        <div class="input-group-prepend">
                            <span class="input-group-text"><i class="fa fa-link"></i></span>
                        </div>
                        <input type="text" name="link" class="form-control" placeholder="Enter url">
                    </div>

                </div>
                <div class="col-md-2 m-md-auto">
                    <button class="btn btn-primary btn-lg btn-block">Short URL</button>
                </div>
            </div>
        </form>
    </div>
</template>

<script>
export default {
    name: "URLShortComponent"
}
</script>

<style scoped>

</style>
