<template>
  <div class="mb-5 mt-3">
    <h5>{{ msg }}</h5>
    <div class="progress">
      <div
        class="progress-bar"
        role="progressbar"
        :style="{ width: (daily / max) * 100 + '%' }"
        :aria-valuenow="daily"
        aria-valuemin="0"
        aria-valuemax="100"
      >
        {{ daily }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Progress",
  props: {
    daily: { type: Number, default: null, required: false },
    max: { type: Number, default: null, required: false },
    msg: { type: String, default: null, required: false }
  }
};
</script>

<style scoped></style>
