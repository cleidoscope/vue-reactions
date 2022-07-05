<script>
import { defineComponent } from 'vue';
import VueReactions from '@/vue-reactions.vue';

export default defineComponent({
  name: 'ServeDev',
  components: {
    VueReactions
  }
});
</script>

<template>
  <div id="app">
    <vue-reactions />
  </div>
</template>
