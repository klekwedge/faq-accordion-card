
<template>
  <details class="accordion-item" :open="activeItem === index">
    <summary class="accordion-item__question active">
      {{ question }}
      <img
        class="accordion-item__icon"
        src="../assets/images/icon-arrow-down.svg"
        alt="click to reveal answer"
      />
    </summary>
    <p class="accordion-item__answer">{{ answer }}</p>
  </details>
</template>

<script  lang="ts">
export default {
  name: "AccordionItem",
  props: {
    question: { type: String, required: true },
    answer: { type: String, required: true },
    activeItem: { type: Number, required: true },
    index: { type: Number, required: true },
  },
};
</script>
  
  <style scoped>
.accordion-item {
  border-bottom: 1px solid var(--dividers-blue-light-grayish);
  padding: 1.2rem 0;
}
.accordion-item__question {
  display: flex;
  align-items: center;
  justify-content: space-between;
  font-size: 1.3rem;
  line-height: 1.6;
  color: var(--neut-blue-very-dark-grayish);
  letter-spacing: 0.01rem;
  cursor: pointer;
  transition: all 0.5s ease;
}

.accordion-item__question:hover {
  color: var(--pri-red-soft);
}

details[open] > .accordion-item__question {
  font-size: 1.3rem;
  font-weight: 700;
  margin-bottom: 0.5rem;
  color: var(--pri-blue-very-dark-desaturated);
}

.accordion-item__icon {
  width: 0.8rem;
  transition: all 0.3s;
}
details[open] .accordion-item__icon {
  transform: rotate(180deg);
}

.accordion-item__answer {
  color: var(--neut-blue-dark-grayish);
  width: 95%;
  opacity: 0;
  line-height: 1.8;
  letter-spacing: 0.004rem;
  transition: all 3s ease;
}

details[open] .accordion-item__answer {
  opacity: 1;
}

@media (min-width: 1440px) {

  .accordion-item__question {
    font-size: 1.4rem;
    padding-right: 1.7rem;
  }

  details[open] > .accordion-item__question {
    font-size: 1.4rem;
  }
}
</style>