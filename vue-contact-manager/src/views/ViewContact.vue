<template>
    <div class="container mt-3">
        <div class="row">
            <div class="col">
                <p class="h3 text-light fw-bold">View Contact</p>
                <p class="text-light fst-italic">Lorem ipsum dolor, sit amet consectetur adipisicing elit. Commodi
                    suscipit voluptates voluptate sed quibusdam animi aspernatur? Vero voluptas excepturi eaque qui
                    tenetur cumque. Accusamus unde rerum eligendi velit porro debitis.</p>
            </div>
        </div>
    </div>
    <div class="container">
        <div class="row align-items-center">
            <div class="col-md-4">
                <img src="https://cdn-icons-png.flaticon.com/512/219/219969.png" class="contact-img-big">
            </div>
            <div class="col-md-6">
                <ul class="list-group">
                    <li class="list-group-item">Name: <span class="fw-bold">Name</span></li>
                    <li class="list-group-item">Email: <span class="fw-bold">Email</span></li>
                    <li class="list-group-item">Mobile: <span class="fw-bold">Mobile</span></li>
                    <li class="list-group-item">Company: <span class="fw-bold">Company</span></li>
                    <li class="list-group-item">Title: <span class="fw-bold">Title</span></li>
                    <li class="list-group-item">Group: <span class="fw-bold">Group</span></li>
                </ul>
            </div>
        </div>
        <div class="row mt-3">
            <div class="col">
                <router-link to="/" class="btn btn-light"><i class="fa fa-arrow-alt-circle-left"></i> Back</router-link>
            </div>
        </div>
    </div>
</template>


<script>
export default {
    name: "ViewContact"
};
</script>   

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>