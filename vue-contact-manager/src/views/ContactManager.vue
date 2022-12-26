<template>
    <div class="container mt-3">
        <div class="row">
            <div class="col">
                <p class="h3 text-light fw-bold">
                    Contact Manager
                    <router-link to="/contacts/add" class="btn btn-light btn-sm"><i
                            class="fa fa-plus-circle"></i> New</router-link>
                </p>
                <p class="text-light fst-italic">Lorem ipsum dolor sit amet consectetur adipisicing elit. Eaque
                    doloribus maxime doloremque suscipit error enim voluptas, ratione autem placeat molestiae libero
                    eius quibusdam alias necessitatibus eum quos aperiam dicta? Recusandae?</p>
                <form>
                    <div class="row">
                        <div class="col-md-6">
                            <div class="row">
                                <div class="col">
                                    <input type="text" class="form-control" placeholder="Search Name">
                                </div>
                                <div class="col">
                                    <input type="submit" class="btn btn-light">
                                </div>
                            </div>
                        </div>
                    </div>
                </form>
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
                        {{ errorMessage}}
                    </p>
                </div>
            </div>
        </div>
    </div>
        <div class="container mt-3" v-if="contacts.length > 0">
            <div class="row">
                <div class="col-md-6" v-for="contact of contacts" :key="contact">
                    <div class="card my-2 list-group-item-light shadow-lg">
                        <div class="card-body">
                            <div class="row align-items-center">
                                <div class="col-sm-4">
                                    <img :src="contact.photo" class="contact-img">
                                </div>
                                <div class="col-sm-7">
                                    <ul class="list-group">
                                        <li class="list-group-item">Name: <span class="fw-bold">{{ contact.name }}</span>
                                        </li>
                                        <li class="list-group-item">Email: <span
                                                class="fw-bold">{{ contact.email }}</span></li>
                                        <li class="list-group-item">Mobile: <span
                                                class="fw-bold">{{ contact.mobile }}</span></li>
                                    </ul>
                                </div>
                                <div class="col-sm-1 d-flex flex-column justify-content-center align-items-center">
                                    <router-link to="/contacts/view/:contactId" class="btn btn-light my-1">
                                        <i class="fa fa-eye"></i>
                                    </router-link>
                                    <router-link to="/contacts/edit/:contactId" class="btn btn-light my-1">
                                        <i class="fa fa-pen"></i>
                                    </router-link>
                                    <button class="btn btn-light my-1">
                                        <i class="fa fa-trash"></i>
                                    </button>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

</template>

<script>
import SpinneR from '@/components/SpinneR.vue';
import { ContactService } from '@/services/ContactService';

export default {
    name: "contactManager",
    data: function () {
        return {
            loading: false,
            contacts: [],
            errorMessage: null
        };
    },
    created: async function () {
        try {
            this.loading = true;
            let response = await ContactService.getAllContacts();
            this.contacts = response.data;
            this.loading = false;
        }
        catch (error) {
            this.errorMessage = error.message;
            this.loading = false;
        }
    },
    methods: {},
    components: { SpinneR }
}
</script>

<style scoped>

</style>