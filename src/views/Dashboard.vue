<template>
  <div class="">
    <div class="overview-list p-5 bg-gray-100 rounded-sm"
         style="--square: 300px">

      <div v-for="field in view"
           :key="field.field"
           class="shadow bg-white rounded-sm flex flex-col p-6 pb-10">
        <h4 class="text-xs uppercase font-bold tracking-wide text-85 pb-8">{{field.field}}</h4>
        <component :is="`widget-${field.view}`"
                   class="my-auto self-center"
                   :value="state[field.field]"
                   :args="state" />
       
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
  data(){
    return {
      view:[
          {
            field:"Test",
            view:"timer"
          }
        ],
        state:{
          Test:45
        }
    }
  }
}
</script>

<style scoped>
.overview-list{
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(var(--square), 1fr));
  /* grid-template-rows: repeat(auto-fill, minmax(var(--square), 1fr)); */
  grid-gap: 1.25rem;
}
</style>