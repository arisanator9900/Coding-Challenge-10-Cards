<script>
import CardFace from "./components/CardFace.vue";

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
      cardList.push({
        value: i,
        visible: false,
      })
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
      :value="card.value"
      :visible="card.visible"
      />
  </section>
</template>

<style>
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
  grid-template-columns: 150px 150px 150px 150px 150px;
  grid-template-rows: 150px 150px;
  column-gap: 5px;
  row-gap: 5px;
  justify-content: center;
}

</style>
