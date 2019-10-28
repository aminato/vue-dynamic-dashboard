<template>
  <ul>
    <li v-for="trophy in value"
        :key="trophy"
        class="text-sm uppercase text-gray-900 flex items-center pb-2"><img class="w-4 mr-2"
           src="https://image.flaticon.com/icons/svg/321/321773.svg"
           alt="trophy icon"> {{trophy}}</li>

  </ul>

</template>

<script>
export default {
  name: "widget-trophies",
  props: ["value"]
};
</script>