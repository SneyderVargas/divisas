<template>
    <v-card>
        <v-card-title class="text-h5 font-weight-regular blue-grey white--text">
            {{ title }}
        </v-card-title>
        <v-card-text>
            <v-subheader class="pa-0">
            </v-subheader>
            <v-autocomplete v-model="model" :items="coint" item-text="name" item-value="id" :readonly="!isEditing"
                :label="`State — ${isEditing ? 'Editable' : 'Readonly'}`" persistent-hint prepend-icon="mdi-city">
            </v-autocomplete>
        </v-card-text>
    </v-card>
</template>

<script>
const axios = require("axios");
const SERVER_URL = process.env.baseUrl;
const APP_ID = process.env.appId;
export default {
    props: ["title"],
    data() {
        return {
            isEditing: true,
            model: null,
            coint: [
                {
                    id: '1',
                    name: APP_ID,
                },
                {
                    id: '2',
                    name: 'nombre2',
                },
                {
                    id: '3',
                    name: 'nombre3',
                }
            ],
        }
    },
    methods: {
        initialize() {
            this.total = 0;
            this.$store.commit("progress", true);
            axios
                .get(`${SERVER_URL}latest.json?app_id=${APP_ID}`, {})
                .then((response) => {
                    console.log(response.data);
                    //this.coint = response.data.data.data;
                    this.$store.commit("progress", false);
                })
                .catch((e) => {
                    let payload = {
                        active: true,
                        type: "error",
                        data: "Error en el proceso",
                    };
                    this.$store.commit("modalAlert", payload);
                    this.$store.commit("progress", false);
                });
        },
    }
}
</script>

<style>
</style>