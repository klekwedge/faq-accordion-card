
<template>
  <section class="accordion">
    <div class="accordion__card">
      <div class="accordion__container">
        <div class="accordion__image" />
        <div class="accordion__shadow" />
      </div>
      <div class="accordion__content">
        <h1 class="accordion__title">FAQ</h1>
        <div class="accordion__questions">
          <AccordionItem
            @click.prevent="() => changeActiveItem(accordion.id)"
            v-for="accordion in faqs"
            :question="accordion.question"
            :activeItem="activeItem"
            :answer="accordion.answer"
            :index="accordion.id"
            :key="accordion.id"
          />
        </div>
      </div>
    </div>
  </section>
</template>


<script  lang="ts">
import { ref } from "vue";
import AccordionItem from "./AccordionItem.vue";
import IFAQ from "./../types/index";

export default {
  name: "AccordionCard",
  components: {
    AccordionItem,
  },
  setup() {
    const activeItem = ref<number>(0);
    const faqs = ref<IFAQ[]>([
      {
        id: 1,
        question: "How many team members can I invite?",
        answer:
          "You can invite up to 2 additional users on the Free plan. There is no limit on team members for the Premium plan.",
      },
      {
        id: 2,
        question: "What is the maximum file upload size?",
        answer:
          "No more than 2GB. All files in your account must fit your allotted storage space.",
      },
      {
        id: 3,
        question: "How do I reset my password?",
        answer:
          "Click “Forgot password” from the login page or Change password” from your profile page. A reset link will be emailed to you.",
      },
      {
        id: 4,
        question: "Can I cancel my subscription?",
        answer:
          "Yes! Send us a message and we'll process your request no questions asked.",
      },
      {
        id: 5,
        question: "Do you provide additional support?",
        answer:
          "Chat and email support is available 24/7. Phone lines are open during normal business hours.",
      },
    ]);

    const changeActiveItem = (newValue: number) => {
      if (activeItem.value === newValue) {
        activeItem.value = 0;
      } else {
        activeItem.value = newValue;
      }
    };

    return {
      faqs,
      activeItem,
      changeActiveItem,
    };
  },
};
</script>

<style scoped>
.accordion {
  margin-top: 6.3rem;
}
.accordion__card {
  position: relative;
  width: 32.7rem;
  height: 53.5rem;
  padding: 13.2rem 2.4rem 4.8rem;
  background: #fff;
  border-radius: var(--border-radius);

  box-shadow: 0 5rem 5rem -2rem rgba(53 18 122 / 0.497159);
}
.accordion__container {
  position: absolute;
  top: -10.8rem;
  left: 50%;
  transform: translate(-50%);
  width: 23.7rem;
  height: auto;
}

.accordion__image {
  z-index: 5;
  height: 18rem;
  width: auto;
  background-image: url("./../assets/images/illustration-woman-online-mobile.svg");
}
.accordion__image::after {
  z-index: -1;
  content: "";
  position: absolute;
  top: 3rem;
  height: 0rem;
  background: transparent;
  width: 100%;
  box-shadow: 0 10rem 7rem 1rem rgba(53 18 122 / 0.497159);
}
.accordion__shadow {
  z-index: -1;
  position: absolute;
  top: 10.8rem;
  left: 0rem;

  width: 24rem;
  height: 14.5rem;

  background-image: url("./../assets/images/bg-pattern-mobile.svg");
  background-repeat: no-repeat;
}

.accordion__title {
  font-size: 3.2rem;
  text-align: center;
  font-weight: 700;
  color: var(--pri-blue-very-dark-desaturated);
  margin-bottom: 1.9rem;
}

.accordion__questions {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  min-height: 29.5rem;
}

@media (min-width: 1440px) {
  .accordion {
    position: relative;
    margin-top: 0;
  }

  .accordion__card {
    width: 92rem;
    height: 50.9rem;
    padding: 6.5rem 9.5rem 8.3rem 47.5rem;
    margin-left: 4.5rem;
    overflow: hidden;
  }

  .accordion::before {
    content: "";
    position: absolute;
    top: 20.3rem;
    left: -4.8rem;
    height: 15rem;
    width: 19.1rem;
    z-index: 99;

    background-image: url("./../assets/images/illustration-box-desktop.svg");
  }
  .accordion::after {
    content: "";
    position: absolute;
    top: 18rem;
    left: 0.3rem;
    width: 9rem;
    height: 0rem;
    box-shadow: 0 12rem 3.5rem 0.5rem rgb(0 0 0);
  }

  .accordion__container {
    top: 48.7%;
    left: -6.7%;
    transform: translate(-10%, -50%);
  }

  .accordion__image {
    position: relative;
    height: 35.9rem;
    width: 47.2rem;
    background-image: url("./../assets/images/illustration-woman-online-desktop.svg");
  }

  .accordion__shadow {
    position: absolute;
    top: -36.5rem;
    left: -49.2rem;
    height: 94.4rem;
    width: 97rem;
    background-image: url("./../assets/images/bg-pattern-desktop.svg");
    background-repeat: no-repeat;
  }

  .accordion__title {
    text-align: left;
  }
}
</style>