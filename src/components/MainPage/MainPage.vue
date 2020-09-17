<template>
  <div class="MainPage">
    <Header title="Covid Statistics" />
    <Table />
  </div>
</template>

<script>
import Header from "@/components/Header";
import Table from "@/components/MainPage/Table";
export default {
  components: { Table, Header },
  props: {}
};
</script>
