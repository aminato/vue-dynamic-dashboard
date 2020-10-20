<template>
  <div>
    <ul class="overflow-y-auto">
      <li
        v-for="athlete in athletes"
        :key="athlete.id"
        class="mb-6 p-6 shadow-md rounded-sm bg-white transform transition-transform scale-95 duration-300 hover:scale-100 hover:-translate-y-1"
      >
        <router-link :to="`athlete/${athlete.id}`">
          <p>{{ athlete.name }}</p>
          <p>{{ athlete.country }}</p>
          <p>{{ athlete.sport }}</p>
        </router-link>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "home",
  data() {
    return {
      athletes: [],
    };
  },
  created() {
    fetch("/athletes.json")
      .then((res) => res.json())
      .then((athletes) => (this.athletes = athletes));
  },
};
</script>
