<template>
    <div class='container'>
        <label>From:</label>
        <br/>
        <select class='form-select' ref='currency' @change="selectCurrency">
			<option value="" selected disabled>Choose</option>
            <option v-for="currency in currencies" v-bind:key="currency.code" >{{currency.code}}</option>
        </select>
        <br/>
        <input type="number" class="form-control" @keyup="inputCurrency" >
    </div>
</template>

<script>
export default {
	props: ['currencies'],
	name: 'ConvertionFrom',
	methods: {
		inputCurrency: function(e) {
			this.value = e.target.value;
			this.$emit('change', {currency: this.currency, value: this.value});
		},
		selectCurrency: function(e) {
			this.currency = e.target.value;
			this.$emit('change', {currency: this.currency, value: this.value});
		}
	},
	data: function() {
		return {
			currencydata: [],
			value: 0
		}
	},
	created: function() {
	// console.log(this.currencies)
	}
}
</script>

<style scoped>

</style>