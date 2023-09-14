
<template>
  <details class="faq-card__questions-container">
    <summary class="faq-card__question active">
      {{ question }}
      <img
        class="faq-card__icon"
        :src="iconArrowDown"
        alt="click to reveal answer"
      />
    </summary>
    <p class="faq-card__answer">{{ answer }}</p>
  </details>
</template>
  
  
  <script  lang="ts">
import { ref } from "vue";

export default {
  name: "AccordionCard",
  props: {
    question: { type: String, required: true },
    answer: { type: String, required: true },
  },
  setup() {
    const faqs = ref([]);

    return {
      faqs,
    };
  },
};
</script>
  
  <style scoped>
.faq-card__questions-container {
  border-bottom: 1px solid var(--dividers-blue-light-grayish);
  padding: 1.2rem 0;
}
.faq-card__question {
  display: flex;
  align-items: center;
  justify-content: space-between;
  font-size: 1.3rem;
  line-height: 1.6;
  color: var(--neut-blue-very-dark-grayish);
  letter-spacing: 0.01rem;
  cursor: pointer;
  transition: margin 0.5s ease;
}

.faq-card__question:hover {
  color: var(--pri-red-soft);
}

details[open] > .faq-card__question {
  font-size: 1.3rem;
  font-weight: 700;
  margin-bottom: 0.5rem;
  color: var(--pri-blue-very-dark-desaturated);
}

.faq-card__icon {
  width: 0.8rem;
  transition: all 0.3s;
}
details[open] .faq-card__icon {
  transform: rotate(180deg);
}

.faq-card__answer {
  color: var(--neut-blue-dark-grayish);
  width: 95%;
  opacity: 0;
  line-height: 1.8;
  letter-spacing: 0.004rem;
  transition: all 3s ease;
}

details[open] .faq-card__answer {
  opacity: 1;
}

@media (min-width: 1440px) {

  .faq-card__question {
    font-size: 1.4rem;
    padding-right: 1.7rem;
  }

  details[open] > .faq-card__question {
    font-size: 1.4rem;
  }

  .faq-card__answer {
  }
}
</style>