<template>
  <v-app>
    <navigation :color="color" :flat="flat" />
    <v-main class="pt-0">
      <first/>
      <home />
      <networks/>
      <about />
      <product />
      <pricing />
      <contact />
    </v-main>
    <v-scale-transition>
      <v-btn
        fab
        v-show="fab"
        v-scroll="onScroll"
        dark
        fixed
        bottom
        right
        color="secondary"
        @click="toTop"
      >
        <v-icon>mdi-arrow-up</v-icon>
      </v-btn>
    </v-scale-transition>
    <foote />
  </v-app>
</template>

<style scoped>
.v-main {
  /* background-image: url("~@/assets/img/circle_moving.gif"); */
  background-image: url("~@/assets/img/black.gif");
  background-attachment: fixed;
  background-position: center;
  background-size: cover;
}
</style>

<script>
import first from "./components/FirstSection";
import navigation from "./components/Navigation";
import foote from "./components/Footer";
import home from "./components/HomeSection";
import networks from "./components/NetworksSection";
import about from "./components/AboutSection";
import product from "./components/ProductSection";
import pricing from "./components/PricingSection";
import contact from "./components/ContactSection";

export default {
  name: "App",

  components: {
    first,
    navigation,
    foote,
    home,
    about,
    product,
    pricing,
    contact,
    networks,
  },

  data: () => ({
    fab: null,
    color: "black",
    flat: null,
  }),

  created() {
    const top = window.pageYOffset || 0;
    if (top <= 60) {
      this.color = "transparent";
      this.flat = true;
    }
  },

  watch: {
    fab(value) {
      if (value) {
        this.color = "secondary";
        this.flat = false;
      } else {
        this.color = "transparent";
        this.flat = true;
      }
    },
  },

  methods: {
    onScroll(e) {
      if (typeof window === "undefined") return;
      const top = window.pageYOffset || e.target.scrollTop || 0;
      this.fab = top > 60;
    },
    toTop() {
      this.$vuetify.goTo(0);
    },
  },
};
</script>
