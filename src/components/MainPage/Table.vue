<template>
  <div>Table</div>
</template>

<script>
import * as axios from "axios";

export default {
  name: "Table",
  mounted() {
    axios
      .get("https://api.thevirustracker.com/free-api?countryTotals=ALL")
      .then(res => {
        console.log(res);
      })
      .catch(err => {
        console.log(err);
      });
  }
};
</script>

<style scoped></style>
