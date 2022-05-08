<template>
  <div class="card" @click="selectCard">
    <div v-if="visible" class="card-face is-front">
      {{ value }}
    </div>
    <div v-else class="card-face is-back">
      <img src="" alt="">
    </div>
  </div>
</template>

<script>
import { Suspense, ref } from "vue";

export default {
  props: {
    value: {
      Number,
      required: true,
    },
    visible: {
      Boolean,
      default: false,
    }
  },
  async setup(props, context) {
    const selectCard = () => {
      console.log(props.value)
      context.emit('select-card', {
        value: props.value,
      })
    }

    let data = ref(null)
    let images = []
    try {
        const results = await fetch("https://dog.ceo/api/breeds/image/random/10");
        data = await results.json()
        return(data)
        //data.message[i] will be the image selected from the json
    }
    catch (e) {
        console.error(e);
    }
  

    return {
      selectCard,
      data
    }
  },
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
