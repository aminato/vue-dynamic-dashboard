<template>
  <div id="app"
       class="bg-indigo-100 min-h-screen sha">
    <nav class="h-40 items-end relative sticky top-0 drop-shadow">
      <div class="clipped bg-indigo-500 absolute inset-0"></div>
      <router-link to="/"
                   class="rounded-full bg-indigo-700 h-32 w-32 flex items-center justify-center shadow shadow-lg uppercase font-bold tracking-widest text-indigo-100 absolute bottom-0 left-50"
                   style="transform:translate(-50%,20%)">Home</router-link>
    </nav>
    <router-view class="px-6 mt-12" />
  </div>
</template>

<style scoped>

.clipped{
  clip-path: polygon(0 0, 100% 0%, 100% 54%, 0% 100%);
  
}

.drop-shadow{
  filter: drop-shadow(0 1px 3px rgba(0, 0, 0, 0.1)) drop-shadow(0 1px 2px  rgba(0, 0, 0, 0.06))
}



</style>