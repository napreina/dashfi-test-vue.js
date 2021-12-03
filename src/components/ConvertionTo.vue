<template>
    <div class='container'>
        <label>To:</label>
        <br/>
        <select class='form-select' ref='currency' @change="selectCurrency">
            <option value="" selected disabled>Choose</option>
            <option v-for="currency in currencies" v-bind:key="currency.code" >{{currency.code}}</option>
        </select>
        <br/>
        <input type="number" class="form-control" v-bind:value="value">
    </div>
</template>

<script>
export default {
    name: 'ConvertionTo',
    props: ['value', 'currencies'],
    data: function() {
        return {
            currency: 'USD',
        }
    },
    methods: {
        selectCurrency: function(e) {
            this.currency = e.target.value;
            this.$emit('change', {currency: this.currency});
        }
    },
    created: function() {
		// console.log(this.currencies)
    },
}
</script>

<style scoped>

</style>