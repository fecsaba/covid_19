<template>
  <div>
    <table class="table">
      <thead>
        <tr>
          <th scope="col">#</th>
          <th scope="col">Name</th>
          <th scope="col">Total cases</th>
          <th scope="col">Total deaths</th>
          <th scope="col">Total serious cases</th>
          <th scope="col">Total recovered</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(country, index) in countries" :key="index">
          <th scope="row">{{ country.ourid }}</th>
          <td>{{ country.title }}</td>
          <td>{{ country.total_cases }}</td>
          <td>{{ country.total_deaths }}</td>
          <td>{{ country.total_serious_cases }}</td>
          <td>{{ country.total_recovered }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import * as axios from "axios";

export default {
  name: "Table",
  mounted() {
    axios
      .get("https://api.thevirustracker.com/free-api?countryTotals=ALL")
      .then(res => {
        this.countries = Object.values(res.data.countryitems[0]);
        this.countries.pop();
        console.log(this.countries);
      })
      .catch(err => {
        console.log(err);
      });
  },
  data() {
    return {
      countries: null
    };
  }
};
</script>

<style scoped></style>
