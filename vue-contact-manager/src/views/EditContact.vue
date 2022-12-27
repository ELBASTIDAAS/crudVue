<template>
    <div class="container mt-3">
        <div class="row">
            <div class="col">
                <p class="h3 text-light fw-bold">Edit Contact</p>
                <p class="text-light fst-italic">Lorem ipsum, dolor sit amet consectetur adipisicing elit. Hic quia
                    vitae, recusandae voluptatem perferendis dicta in! Voluptatibus repellat officiis rerum soluta
                    delectus amet, id quod, fugit, est tempore hic doloribus.</p>
            </div>
        </div>
    </div>
    <div class="container mt-3">
        <div class="row">
            <div class="col-md-4">
                <form @submit.prevent="updateSubmit()">
                    <div class="mb-2">
                        <input required v-model="contact.name" type="text" class="form-control" placeholder="Name">
                    </div>
                    <div class="mb-2">
                        <input required v-model="contact.photo" type="text" class="form-control" placeholder="Photo URL">
                    </div>
                    <div class="mb-2">
                        <input required v-model="contact.email" type="email" class="form-control" placeholder="Email">
                    </div>
                    <div class="mb-2">
                        <input required v-model="contact.mobile" type="number" class="form-control" placeholder="Mobile">
                    </div>
                    <div class="mb-2">
                        <input required v-model="contact.company" type="text" class="form-control" placeholder="Company">
                    </div>
                    <div class="mb-2">
                        <input required v-model="contact.title" type="text" class="form-control" placeholder="Title">
                    </div>
                    <div class="mb-2">
                        <select required v-model="contact.groupId" class="form-control" v-if="groups.length > 0">
                            <option value="">Select Group</option>
                            <option :value="group.id" v-for="group in groups" :key="group.id">{{ group.name }}</option>
                        </select>
                    </div>
                    <div class="mb-2">
                        <input type="submit" class="btn btn-light" value="Update">
                    </div>
                </form>
                <div class="ml-10">
                    <div>
                        <router-link to="/" class="btn btn-dark"><i class="fa fa-arrow-alt-circle-left"></i>
                            Back</router-link>
                    </div>
                </div>
            </div>
            <div class="col-md-4">
                <img :src="contact.photo" class="contact-img">
            </div>
        </div>
    </div>
</template>

<script>
// import SpinneRVue from '@/components/SpinneR.vue';
import { ContactService } from '../services/ContactService.js';
export default {
    name: 'editContact',
    components: {
        // SpinneRVue
    },
    data: function () {
        return {
            contactId: this.$route.params.contactId,
            loading: false,
            contact: {
                name: '',
                photo: '',
                email: '',
                mobile: '',
                company: '',
                title: '',
                group: '',
                groupId: '',
            },
            errorMessages: null,
            groups: []
        }
    },
    created: async function () {
        try {
            this.loading = true;
            let response = await ContactService.getContact(this.contactId);
            let groupsResponse = await ContactService.getAllGroups();
            this.contact = response.data;
            this.groups = groupsResponse.data;
            this.loading = false;
        } catch (error) {
            this.errorMessages = error;
            this.loading = false;
        }
        this.loading = false;
    },
    methods: {
        updateSubmit: async function () {
            try {
                let response = await ContactService.updateContact(this.contact, this.contactId);
                if (response) {
                    return this.$router.push('/')
                } else {
                    return this.$router.push(`/contacts/edit/${this.contactId}`)
                }
            } catch (error) {
                console.log(error)
            }
        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>