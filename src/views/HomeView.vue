<template>
  <div class="State Data"></div>
</template>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      name: "StateData",
      states: [],
      currentState: {},
      stateFilter: "",
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
    filterStates: function () {
      return this.states.filter((state) => {
        var lowerTitle = state.title.toLowerCase();
        var lowerTitleFilter = this.stateFilter.toLowerCase();
        return lowerTitle.includes(lowerTitleFilter);
      });
    },
  },
};
</script>
