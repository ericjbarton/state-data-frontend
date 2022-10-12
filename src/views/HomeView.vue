<template>
  <div class="Home"></div>
  <div v-for="state in states" v-bind:key="state.id">
    <h3>{{ state.state }}</h3>
    <p>Median Household Income</p>
    <h5>{{ state.median_household_income }}</h5>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      name: "StateData",
      states: [],
      currentState: {},
    };
  },
  created: function () {
    this.indexStates();
  },
  methods: {
    indexStates: function () {
      axios.get("/states.json").then((response) => {
        this.states = response.data;
        console.log("All States:", this.states);
      });
    },
  },
};
</script>
