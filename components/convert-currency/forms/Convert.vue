<template>
    <v-form ref="form" v-model="valid" lazy-validation>
        <v-text-field type="number" v-model="monto" :counter="10" :rules="montoRules" label="Monto" required>
        </v-text-field>
        <SelectCoint :title="'Moneda origen'" />
        <v-text-field v-model="email" :rules="emailRules" label="E-mail" required></v-text-field>
        <v-select v-model="select" :items="items" :rules="[v => !!v || 'Item is required']" label="Item" required>
        </v-select>
        <v-btn :disabled="!valid" color="success" class="mr-4" @click="convertir">
            Convertir
        </v-btn>
    </v-form>
</template>
<script>
import SelectCoint from "@/components/convert-currency/controls/SelectCoint";
export default {
    components: {
        SelectCoint
    },
    data: () => ({
        valid: true,
        monto: '',
        montoRules: [
            v => !!v || 'Name is required',
            v => (v && v.length <= 10) || 'Name must be less than 10 characters',
        ],
        email: '',
        emailRules: [
            v => !!v || 'E-mail is required',
            v => /.+@.+\..+/.test(v) || 'E-mail must be valid',
        ],
        select: null,
        items: [
            'Item 1',
            'Item 2',
            'Item 3',
            'Item 4',
        ],
    }),

    methods: {
        convertir() {
            if (this.$refs.form.validate()) {

            } else {

            }
        }
    }
}
</script>

<style>
</style>