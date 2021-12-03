<template>
    <div class="convertion-container">
      <div class="convertion">
        <div class="from">
          <convertion-from :currencies="currencies" @change="getFromValue"></convertion-from>
        </div>
        <div class="to">
          <convertion-to :currencies="currencies" @change="getFromTo" v-bind:value="toValue"></convertion-to>
        </div>
      </div>

      <button class="btn btn-success btn-lg" @click="convert">Convert</button>
    </div>
</template>

<script>
import ConvertionFrom from './ConvertionFrom.vue';
import ConvertionTo from './ConvertionTo.vue';
export default {
  name: 'Convertion',
  components: {
    ConvertionFrom,
    ConvertionTo
  },
  data: function() {
    return {
      currencies: [],
      fromValue: 0,
      fromCurrency: 'USD',
      toCurrency: 'USD',
      toValue: 0
    }
  },
  methods: {
    getFromValue: function(obj) {
      this.fromValue = obj.value;
      this.fromCurrency = obj.currency;
    },
    getFromTo: function(obj) {
      this.toCurrency = obj.currency
    },
    convert: function() {
      console.log(this.fromCurrency);
      console.log(this.fromCurrency);
      console.log(this.fromValue);
      this.getExchangedAmount(this.fromCurrency,this.toCurrency,this.fromValue);
    },
    async getData() {
      try {
        const response = await this.$http.get(
          "http://localhost:8000/api/currencies"
        );
        // JSON responses are automatically parsed.
        this.currencies = response.data.data
      } catch (error) {
        console.log(error);
      }
    },
    async getExchangedAmount(from, to, amount) {
      const params = {from:from, to:to, amount:amount};
      try {
        const response = await this.$http.post(
          "http://localhost:8000/api/exchange",
          params
        );
        // JSON responses are automatically parsed.
        this.toValue = response.data.data['amount_exchanged']
      } catch (error) {
        console.log(error);
      }
    }
  },
  mounted() {
    this.getData();
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .convertion-container {
    height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 20px;
  }
  .convertion {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
  }
</style>
