<template>
  <div>
    <ul class="overflow-y-auto">
      <li v-for="athlete in athletes"
          :key="athlete.id"
          class="mb-6 p-6 shadow-md rounded-sm bg-white">
        <div>
          <p>
            {{athlete.name}}
          </p>
          <p>
            {{athlete.country}}
          </p>
        </div>
        <div class="flex justify-between">
          <p>
            {{athlete.sport}}
          </p>
          <router-link :to="`athlete/${athlete.id}`"
                       class="text-xs uppercase">show more</router-link>
        </div>
      </li>

    </ul>
  </div>
</template>

<script>
export default {
  name: "home",
  data() {
    return {
      athletes: []
    };
  },
  created() {
    fetch("/athletes.json")
      .then(res => res.json())
      .then(athletes => (this.athletes = athletes));
  }
};
</script>
