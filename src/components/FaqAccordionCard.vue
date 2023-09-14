
<template>
  <article class="faq">
    <div class="faq-card"></div>
  </article>
</template>


<script  lang="ts">
import { ref } from "vue";

export default {
  name: "FaqAccordionCard",
  setup() {
    const faqs = ref([]);

    return {
      faqs,
    };
  },
};
</script>

<style scoped>
</style>