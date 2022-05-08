<script>
import CardFace from "./components/CardFace.vue";
import { Suspense, ref } from "vue";

export default {
  name: "App",
  components: {
    CardFace,
  },
  setup() {
    const cardList = []
    // const data = ref(null)
    // try {
    //     const res = await fetch('api')
    //     data.value = res.json()
    // }
    // catch (e) {
    //     console.error(e)
    // }

    // const cardList = [];

    for (let i = 0; i < 10; i++) {
      cardList.push(i);
    }

    return {
      cardList
    };
  },
};
</script>

<template>
  <h1 class="title">Dog Api Card Flipper</h1>
    <section class="card-container">
      <CardFace 
      v-for="(card, index) in cardList"
      :key="`card-${index}`"
      :value="card"
      />
  </section>
</template>

<style>
:root {
  --white: #ffffff;
  --white-soft: #f8f8f8;
  --white-mute: #f2f2f2;

  --black: #181818;
  --black-soft: #222222;
  --black-mute: #282828;

  --indigo: #2c3e50;

  --light-1: rgba(60, 60, 60, 0.29);
  --light-2: rgba(60, 60, 60, 0.12);
  --dark-1: rgba(84, 84, 84, 0.65);
  --dark-2: rgba(84, 84, 84, 0.48);

  --light-1: var(--indigo);
  --light-2: rgba(60, 60, 60, 0.66);
}

* {
  margin: 0;
  padding: 0;
}

.title {
  text-align: center;
  margin: 10px;
  padding: 10px;
}

.card-container {
  display: grid;
  grid-template-columns: 100px 100px 100px 100px 100px;
  grid-template-rows: 100px 100px;
  column-gap: 30px;
  row-gap: 30px;
  justify-content: center;
}

.card {
  border: 5px solid #ccc;
}
</style>
