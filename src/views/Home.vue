<template>
  <div class="home">
    <input type="text" v-model="zipcode" />
    <button @click="autoInput">住所自動入力</button>
    <p>Address : {{ streetAddress }}</p>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      zipcode: "",
      streetAddress: "",
    };
  },
  methods: {
    async autoInput() {
      const item = await axios.get(
      `https://apis.postcode-jp.com/api/v4/postcodes/${this.zipcode}?apiKey=LNEVeEDfhmbPhT2xlhlQMRBYLkXpAI9DXYMwVT8`
    );
      console.log(item.data)
      this.streetAddress = item.data[0].allAddress;
    }
  }
}
</script>

<style>
.home {
  padding: 10px;
}

p {
  padding: 20px 0;
}
</style>