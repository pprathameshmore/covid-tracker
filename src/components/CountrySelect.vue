<template>
    <select @change="onCountryChange()" v-model="selected" class="form-select block w-full border p-3 rounded mt-10">
        <option value="0">
            Select country
        </option>
        <option v-for="country in countries" :value="country.ID">
            {{ country.Country }}
        </option>
    </select>
</template>

<script>
export default {
    name : "CountrySelect",
    props: ['countries'],
    data() {
        return {
            selected: 0
        }
    },
    methods: {
        onCountryChange() {
            const country = this.countries.find((item) => item.ID === this.selected)
            console.log('Country', country)
            this.$emit('get-country', country)
        }
    }
}
</script>