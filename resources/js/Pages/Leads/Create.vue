<template>
    <layout>
        <div class="container">
            <nav aria-label="breadcrumb">
                <ol class="breadcrumb bg-transparent p-0">
                    <li class="breadcrumb-item"><inertia-link :href="$route('lead.index')">Leads</inertia-link></li>
                    <li class="breadcrumb-item active" aria-current="page">Create Lead</li>
                </ol>
            </nav>

            <h1 class="mb-4">Create Lead</h1>

            <div class="card mb-4">
                <div class="card-header">
                    <h2 class="h5 mb-0">Lead details</h2>
                </div>

                <div class="card-body">
                    <form @submit.prevent="handleSubmit">
                        <div class="row">
                            <div class="col-md-6">
                                <div class="form-group">
                                    <label for="name">Name</label>
                                    <input id="name" class="form-control" v-model="lead.name" tabindex="1">
                                </div>

                                <div class="form-group">
                                    <label for="phone">Phone</label>
                                    <input id="phone" class="form-control" v-model="lead.phone" tabindex="3">
                                </div>

                                <div class="form-group">
                                    <label for="package">Interested Package</label>
                                    <input id="package" class="form-control" v-model="lead.package" tabindex="5">
                                </div>
                            </div>

                            <div class="col-md-6">
                                <div class="form-group">
                                    <label for="name">Email Address</label>
                                    <input id="name" class="form-control" v-model="lead.email" tabindex="2">
                                </div>

                                <div class="form-group">
                                    <label for="date_of_birth">Date of Birth</label>
                                    <input type="date" id="date_of_birth" class="form-control" v-model="lead.date_of_birth" tabindex="4">
                                </div>
                            </div>
                        </div>

                        <button class="btn btn-primary mr-2">Create Lead</button>
                        <inertia-link class="btn btn-light" :href="$route('lead.index')">Back</inertia-link>
                    </form>
                </div>
            </div>
        </div>
    </layout>
</template>

<script>
import Layout from '../../Shared/Layout';

export default {
    components: { Layout },

    data() {
        return {
            'lead': {
                'name': '',
                'email': '',
                'phone': '',
                'date_of_birth': '',
                'age': '',
                'package': ''
            }
        }
    },

    methods: {
        async handleSubmit() {
            let response = await this.$inertia.post('/leads/save', this.lead)
        }
    }
};
</script>
