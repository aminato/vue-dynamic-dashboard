<template>
  <div>
    
    <div class="flex items-baseline justify-center">
      <div class="text-center px-3">
        <p class="text-lg text-gray-900">{{time.hours}}</p>
        <p class="text-xs text-gray-600 uppercase pt-1">hours</p>
      </div>

      <p class="text-lg text-gray-900">:</p>

      <div class="text-center px-3">
        <p class="text-lg text-gray-900">{{time.minutes}}</p>
        <p class="text-xs text-gray-600 uppercase pt-1">minutes</p>
      </div>

      <p class="text-lg text-gray-900">:</p>

      <div class="text-center px-3">
        <p class="text-lg text-gray-900">{{time.seconds}}</p>
        <p class="text-xs text-gray-600 uppercase pt-1">seconds</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "widget-timer",
  props: ["value"],
  computed: {
    time() {
      let time = {
        hours: "00",
        minutes: "00",
        seconds: "00"
      };

      if (this.value) {
        let date = new Date(null);
        date.setSeconds(this.value);
        const string = date.toISOString().substr(11, 8);

        [time.hours, time.minutes, time.seconds] = string.split(":");
      }

      return time;
    }
  }
};
</script>