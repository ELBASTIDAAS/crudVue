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

    <!-- Spinner -->
    <div v-if="loading">
        <div class="container">
            <div class="row">
                <div class="col">
                    <SpinneR />
                </div>
            </div>
        </div>
    </div>

    <!-- Error message -->
    <div v-if="!loading && errorMessage">
        <div class="container mt-3">
            <div class="row">
                <div class="col">
                    <p class="h4 text-danger fw-bold">
                        {{ errorMessage }}
                    </p>
                </div>
            </div>
        </div>
    </div>

    <div class="container" v-if="!loading && isDone()">
        <div class="row align-items-center">
            <div class="col-md-4">
                <img :src="contact.photo" class="contact-img-big">
            </div>
            <div class="col-md-6">
                <ul class="list-group">
                    <li class="list-group-item">Name: <span class="fw-bold">{{ contact.name }}</span></li>
                    <li class="list-group-item">Email: <span class="fw-bold">{{ contact.email }}</span></li>
                    <li class="list-group-item">Mobile: <span class="fw-bold">{{ contact.mobile }}</span></li>
                    <li class="list-group-item">Company: <span class="fw-bold">{{ contact.company }}</span></li>
                    <li class="list-group-item">Title: <span class="fw-bold">{{ contact.title }}</span></li>
                    <li class="list-group-item">Group: <span class="fw-bold">{{ group.name }}</span></li>
                </ul>
            </div>
        </div>
        <div class="row mt-3">
            <div class="col">
                <router-link to="/" class="btn btn-dark"><i class="fa fa-arrow-alt-circle-left"></i> Back</router-link>
            </div>
        </div>
    </div>
</template>


<script>
import SpinneR from '@/components/SpinneR.vue';
import { ContactService } from '@/services/ContactService';


export default {
    name: "ViewContact",
    data() {
        return {
            contactId: this.$route.params.contactId,
            loading: false,
            contact: {},
            errorMessage: null,
            group: {}
        };
    },
    created: async function () {
        try {
            this.loading = true;
            let response = await ContactService.getContact(this.contactId);
            let groupResponse = await ContactService.getGroup(response.data);
            this.contact = response.data;
            this.group = groupResponse.data;
            this.loading = false;
        } catch (error) {
            this.errorMessage = error.message;
            this.loading = false;
        }
    },
    components: {
        SpinneR
    },
    methods: {
        isDone: function () {
            return Object.keys(this.contact).length > 0 && Object.keys(this.group).length > 0;
        }
    }
};
</script>   

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>