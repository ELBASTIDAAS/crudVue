<template>
    <div class="container mt-3">
        <div class="row">
            <div class="col">
                <p class="h3 text-light fw-bold">Edit Contact</p>
                <p class="text-light fst-italic">Lorem ipsum, dolor sit amet consectetur adipisicing elit. Hic quia vitae, recusandae voluptatem perferendis dicta in! Voluptatibus repellat officiis rerum soluta delectus amet, id quod, fugit, est tempore hic doloribus.</p>
            </div>
        </div>
    </div>
    <div class="container mt-3">
        <div class="row">
            <div class="col-md-4">
                <form>
                    <div class="mb-2">
                        <input type="text" class="form-control" placeholder="Name">
                    </div>
                    <div class="mb-2">
                        <input type="text" class="form-control" placeholder="Photo URL">
                    </div>
                    <div class="mb-2">
                        <input type="email" class="form-control" placeholder="Email">
                    </div>
                    <div class="mb-2">
                        <input type="number" class="form-control" placeholder="Mobile">
                    </div>
                    <div class="mb-2">
                        <input type="text" class="form-control" placeholder="Company">
                    </div>
                    <div class="mb-2">
                        <input type="text" class="form-control" placeholder="Title">
                    </div>
                    <div class="mb-2">
                        <select class="form-control">
                            <option value="">Select Group</option>
                        </select>
                    </div>
                    <div class="mb-2">
                        <input type="submit" class="btn btn-light" value="Update">
                    </div>
                </form>
            </div>
            <div class="col-md-4">
                <img src="https://cdn-icons-png.flaticon.com/512/219/219969.png" class="contact-img">
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'editContact'
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>