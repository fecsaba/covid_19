<template>
  <div>
    <Header title="Details"></Header>
    <Card :details-obj="det" :countryName="countryName" />
  </div>
</template>

<script>
import Header from "@/components/Header";
import Card from "@/components/Details/Card";
export default {
  name: "Details",
  components: { Card, Header },
  created() {
    this.det = this.$route.params.details;
    this.countryName = this.$route.params.countryName;
    // console.log(this.det)
  },
  data() {
    return {
      det: null,
      countryName: null
    };
  }
};
</script>

<style scoped></style>
