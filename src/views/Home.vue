<template>
  <div class="home">
    <HelloWorld />
    <!-- <AutoComplete /> -->
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue';
import AutoComplete from '@/components/AutoComplete';

export default {
  name: 'home',
  components: {
    HelloWorld,
    AutoComplete
  },
};
</script>

<style scoped>

</style>
