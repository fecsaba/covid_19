<template>
  <div class="card text-center">
    <div class="card-header">
      <h3 class="display-4">
        {{ date }}
      </h3>
    </div>
    <div class="card-body">
      <div class="mb-3">
        <h5 class="card-title display-4">{{ countryName }}</h5>
      </div>
      <p class="card-text"></p>
      <Progress :max="maxCases" :daily="dailyCases" :msg="'Daily Cases'" />
      <Progress :max="maxDeaths" :daily="dailyDeaths" :msg="'Daily Deaths'" />
      <form>
        <div class="form-group">
          <label for="formControlRange">Date</label>
          <input
            type="range"
            class="form-control-range"
            id="formControlRange"
            min="0"
            :max="daysCount"
            v-model="i"
          />
        </div>
      </form>
    </div>
    <div class="card-footer text-muted">
      <button class="btn btn-primary" @click="goHome()">Go back</button>
    </div>
  </div>
</template>

<script>
import Progress from "@/components/Details/Progress";
import router from "@/router";
export default {
  name: "Card",
  components: { Progress },
  props: {
    countryName: { type: String, default: null, required: false },
    detailsObj: { type: Object, default: null, required: false }
  },
  mounted() {
    this.anim();
  },
  methods: {
    anim() {
      console.log("mounted");
      this.i = 0;
      this.daysCount = Object.keys(this.detailsObj).length - 2;
      const days = Object.keys(this.detailsObj);
      const valueArr = Object.values(this.detailsObj);
      valueArr.pop();
      days.pop();
      const dailyCases = valueArr.map(o => o.new_daily_cases);
      const dailyDeaths = valueArr.map(o => o.new_daily_deaths);
      this.maxCases = Math.max(...dailyCases);
      this.maxDeaths = Math.max(...dailyDeaths);
      // console.log(dailyCases);
      const step = () => {
        this.date = days[this.i];
        this.dailyCases = valueArr[this.i].new_daily_cases;
        this.dailyDeaths = valueArr[this.i].new_daily_deaths;
        // console.log(days[i]);
        if (this.i === this.daysCount) {
          clearInterval(si);
        }
        this.i++;
      };

      let si = setInterval(step, 1000);
    },
    goHome() {
      router.back()
    }
  },
  data() {
    return {
      date: null,
      maxCases: 0,
      maxDeaths: 0,
      dailyCases: 0,
      dailyDeaths: 0,
      daysCount: 0,
      i: 0
    };
  }
};
</script>

<style scoped></style>
