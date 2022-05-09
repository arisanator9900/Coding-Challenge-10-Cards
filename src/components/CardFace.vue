<template>
  <div class="card" @click="selectCard">
    <div v-if="visible" class="card-face is-front">
      {{ value }}
    </div>
    <div v-else class="card-face is-back">
      <DogImages :imageNum="value"/>
      <!-- <img src="" alt=""> -->
    </div>
  </div>
</template>

<script>
import { Suspense, ref } from "vue";
import DogImages from "./DogImages.vue";


export default {
    props: {
        value: {
            Number,
            required: true,
        },
        visible: {
            Boolean,
            default: false,
        },
    },
    setup(props, context) {
        const selectCard = () => {
            console.log(props.value);
            context.emit("select-card", {
                value: props.value,
            });
        };
        return {
            selectCard,
        };
    },
    components: {DogImages},
};
</script>

<style>

.card {
  text-align: center;
  padding: 10px;
  border: 5px solid #ccc;
  position: relative;
}

.card-face {
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0;
  left: 0;
}

.card-face.is-front {
  background-color: red;
  color: white;
}

.card-face.is-back {
  background-color: blue;
  color: white;
}
</style>
