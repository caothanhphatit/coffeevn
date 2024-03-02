User
<template>
  <v-app-bar>
    <v-app-bar-title color="basil">
      <h1 class="font-weight-bold text-h2 text-basil">
        Café Việt
      </h1></v-app-bar-title
    >
    <v-tabs v-model="tab" bg-color="transparent" color="basil" grow>
      <v-tab v-for="item in items" :key="item" :value="item">
        {{ item }}
      </v-tab>
    </v-tabs>

    <v-btn icon>
      <v-icon>mdi-magnify</v-icon>
    </v-btn>

    <v-btn icon @click="openCart">
      <v-icon>mdi-cart</v-icon>
      <v-badge color="red" :content="cartItemCount" overlap>
        <template v-slot:badge>{{ cartItemCount }}</template>
      </v-badge>
    </v-btn>

    <v-btn icon>
      <v-icon>mdi-login</v-icon>
    </v-btn>
  </v-app-bar>

  <v-window v-model="tab">
    <v-window-item v-for="item in items" :key="item" :value="item">
      <v-card-text>
        <v-window v-model="tab">
          <v-window-item value="Trang chủ">
            <Hometab @navigateToTab="navigateToTab" />
          </v-window-item>

          <v-window-item value="Phin Cafe"> coming soon ... </v-window-item>

          <v-window-item value="Cafe">
            <Coffeetab @addToCartEvent="addToCartEvent" />
          </v-window-item>

          <v-window-item value="Cafe"> coming soon ... </v-window-item>

          <v-window-item value="Liên Hệ"> coming soon ... </v-window-item>

          <v-window-item value="Mua Hàng"> coming soon ... </v-window-item>
        </v-window>
      </v-card-text>
    </v-window-item>
  </v-window>
</template>

<script>
import Cookies from "js-cookie";
import Hometab from "../components/Hometab.vue";
import Coffeetab from "../components/Coffeetab.vue";

export default {
  data() {
    return {
      tab: "Trang chủ",
      items: ["Trang chủ", "Phin Cafe", "Cafe", "Liên Hệ", "Mua Hàng"],
      cartItemCount: 0, // Initialize cartItemCount
    };
  },

  computed: {
    cartItemCountFromCookies() {
      let cartItems = Cookies.get("cartItems") || "{}";
      cartItems = JSON.parse(cartItems);
      let count = 0;
      Object.values(cartItems).forEach((quantity) => {
        count += quantity;
      });
      return count;
    },
  },

  methods: {
    navigateToTab(tabIndex) {
      this.tab = this.items[tabIndex];
    },

    addToCartEvent() {  
      console.log("D")
      this.cartItemCount = this.cartItemCountFromCookies; // Remove parentheses ()
    },
  },
  components: {
    Hometab,
    Coffeetab,
  },
  created() {
    this.cartItemCount = this.cartItemCountFromCookies; // Remove parentheses ()
  },
  watch: {
    cartItemCountFromCookies: {
      handler(newCount) {
        this.cartItemCount = newCount;
      },
      immediate: true, // Thực hiện ngay lập tức khi tạo instance
    },
  },

};
</script>


<style>
/* Helper classes */
.bg-basil {
  background-color: #fffbe6 !important;
}
.text-basil {
  color: #356859 !important;
}
</style>