<script>
import CardFace from "./components/CardFace.vue";
import { ref } from "vue";

export default {
  name: "App",
  components: {
    CardFace,
  },
  setup() {
    const cardList = ref([])
    // const data = ref(null)
    // try {
    //     const res = await fetch('api')
    //     data.value = res.json()
    // }
    // catch (e) {
    //     console.error(e)
    // }

    for (let i = 0; i < 10; i++) {
      cardList.value.push({
        value: i,
        visible: false,
      })
    }

    const flipCard = (payload) => {
      cardList.value[payload.value].visible = true;
    }

    return {
      cardList,
      flipCard,
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
      :value="card.value"
      :visible="card.visible"
      @selectCard="flipCard"
      />
  </section>
</template>

<style>
* {
  margin: 0;
  padding: 0;
  font-family: Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
}

.title {
  text-align: center;
  margin: 10px;
  padding: 10px;
}

.card-container {
  display: grid;
  grid-template-columns: 150px 150px 150px 150px 150px;
  grid-template-rows: 150px 150px;
  column-gap: 5px;
  row-gap: 5px;
  justify-content: center;
}

</style>
