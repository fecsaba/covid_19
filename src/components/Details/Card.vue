<template>
  <div class="card text-center">
    <div class="card-header">
      Featured
    </div>
    <div class="card-body">
      <h5 class="card-title">{{ countryName }}</h5>
      <p class="card-text">
        With supporting text below as a natural lead-in to additional content.
      </p>
      <a href="#" class="btn btn-primary">Go somewhere</a>
    </div>
    <div class="card-footer text-muted">
      2 days ago
    </div>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: {
    countryName: { type: String, default: null, required: false },
    detailsObj: { type: Object, default: null, required: false }
  },
  mounted() {
    this.anim();
  },
  methods: {
    anim() {
      // const days = Object.keys(this.detailsObj).length - 2;
      const valueArr = Object.values(this.detailsObj);
      valueArr.pop();
      console.log(valueArr);
    }
  }
};
</script>

<style scoped></style>
