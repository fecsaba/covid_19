<template>
  <div>
    <h1 class="display-1">{{ title }}</h1>
  </div>
</template>

<script>
export default {
  name: "Header",
  props: {
    title: { type: String, default: null, required: false }
  }
};
</script>

<style scoped></style>
