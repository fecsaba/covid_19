<template>
  <div>
    <table class="table">
      <thead>
        <tr>
          <th scope="col">#</th>
          <th scope="col">First</th>
          <th scope="col">Last</th>
          <th scope="col">Handle</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th scope="row">1</th>
          <td>Mark</td>
          <td>Otto</td>
          <td>@mdo</td>
        </tr>
        <tr>
          <th scope="row">2</th>
          <td>Jacob</td>
          <td>Thornton</td>
          <td>@fat</td>
        </tr>
        <tr>
          <th scope="row">3</th>
          <td>Larry</td>
          <td>the Bird</td>
          <td>@twitter</td>
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
        console.log(Object.values(res.data.countryitems[0]));
        this.countries = Object.values(res.data.countryitems[0]);
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
