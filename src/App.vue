<template>
  <div class="home">
    <input type="text" v-model="zipcode" maxlength="7" />
    <button @click="addressInfo">住所自動入力</button>
    <p>Address：{{ addressData }}</p>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      zipcode: null,
      addressData: "",
      apiKey: "deWIKvQg3Cdrcvb2gmVWHtjIJTMin2Z4fRoi1cn",
    };
  },
  methods: {
    addressInfo() {
      let url =
        "https://apis.postcode-jp.com/api/v3/postcodes/" +
        this.zipcode +
        "?apiKey=" +
        this.apiKey;
      axios.get(url).then((res) => {
        this.addressData = res.data.allAddress;
      });
    },
  },
};
</script>


