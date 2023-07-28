<template>
  <layout>
    <router-view />
  </layout>
</template>

<script>
import { ref } from "vue";
import layout from "./layouts/defaultLayout";

export default {
  name: "LayoutDefault",

  components: {
    layout,
  },

  setup() {
    return {
      leftDrawerOpen: ref(false),
    };
  },
};
</script>
