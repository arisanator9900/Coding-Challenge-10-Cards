<script>
import CardFace from "./components/CardFace.vue";
import DogImages from "./components/DogImages.vue";
import { Suspense, ref } from "vue";



export default {
  components: {
    CardFace,
  },
  setup() {
    const cardList = ref([])

    for (let i = 0; i < 10; i++) {
      cardList.value.push({
        value: i,
        visible: false,
      })
    }

    const flipCard = (payload) => {
      //inverts the values to flip the cards
      cardList.value[payload.value].visible = !cardList.value[payload.value].visible;
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
  <Suspense>
    <template #default>
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
    <template #fallback>
        <div class="loading">
          Loading please wait ...
        </div>
    </template>
  </Suspense>
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

.loading {
  text-align: center;
  width: 100%;
  margin-top: 10px;
}

</style>
