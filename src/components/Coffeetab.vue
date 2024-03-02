<template>
  <v-app>
    <Coffeecard @addToCartEvent="addToCartEvent"></Coffeecard>
  </v-app>
</template>

<script>
import Coffeecard from "./Coffeecard.vue";
export default {
  components: {
    Coffeecard,
  },
  methods: {
    addToCartEvent() {
      this.$emit("addToCartEvent");
    },
  },
};
</script>
