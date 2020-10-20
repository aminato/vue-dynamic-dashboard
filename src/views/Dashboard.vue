<template>
  <div class="">
    <div class="overview-list p-5"
         style="--square: 300px"
         v-if="stats">

      <div v-for="card in view"
           :key="card.field"
           class="shadow bg-white rounded-sm flex flex-col p-6 pb-10">
        <h4 class="text-xs uppercase font-bold tracking-wide text-85 pb-8">{{card.field}}</h4>
        <component :is="`widget-${card.view}`"
                   class="my-auto self-center"
                   :value="stats[card.field]"
                   :args="stats" />

      </div>
    </div>
  </div>
</template>

<script>
const required = require.context("../components/widgets", false, /\.vue$/);
export default {
  name: "Dashboard",
  beforeCreate: function() {
    required.keys().forEach(fileName => {
      const componentConfig = required(fileName);
      let componentName = componentConfig.default.name;

      this.$options.components[componentName] =
        componentConfig.default || componentConfig;
    });
  },
  created() {
    fetch(`/athletes/${this.$route.params.id}.json`)
      .then(res => res.json())
      .then(stats => (this.stats = stats));
  },
  computed: {
    view() {
      if (!this.stats) return [];
      return this.views[this.stats.sport];
    }
  },
  data() {
    return {
      stats: null,
      views: {
        basket: [
          {
            field: "name",
            view: "raw"
          },
          {
            field: "sport",
            view: "raw"
          },
          {
            field: "country",
            view: "raw"
          },
          {
            field: "assistsPerGame",
            view: "raw"
          },
          {
            field: "assists",
            view: "raw"
          },
          {
            field: "steals",
            view: "raw"
          },
          {
            field: "points",
            view: "raw"
          },
          {
            field: "rebounds",
            view: "raw"
          },
          {
            field: "team",
            view: "raw"
          },
          {
            field: "teamLogo",
            view: "img"
          },
          {
            field: "playedAvg",
            view: "timer"
          },
          {
            field: "FG",
            view: "raw"
          }
        ],
        athletics: [
          {
            field: "name",
            view: "raw"
          },
          {
            field: "sport",
            view: "raw"
          },
          {
            field: "country",
            view: "raw"
          }
        ],
         soccer: [
          {
            field: "name",
            view: "raw"
          },
          {
            field: "sport",
            view: "raw"
          },
          {
            field: "country",
            view: "raw"
          },
          {
            field: "assistsPerGame",
            view: "raw"
          },
          {
            field: "assists",
            view: "raw"
          },
          {
            field: "goals",
            view: "raw"
          },
          {
            field: "team",
            view: "raw"
          },
          {
            field: "teamLogo",
            view: "img"
          },
        ],
      }
    };
  }
};
</script>

<style scoped>
.overview-list{
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(var(--square), 1fr));
  /* grid-template-rows: repeat(auto-fill, minmax(var(--square), 1fr)); */
  grid-gap: 1.25rem;
}
</style>
