<template lang="pug">
ul#side-menu.hidden.menu-nav(
  :class="['md:block', { 'show': menu_visibility }]"
)
  li(
    v-for="(menu, key) in menus",
    :class="{ 'active': current_block == key }",
    @click="scroll(key)"
  )
    i
    span.text-gray-200 {{ menu.name }}
</template>

<script>
import menus from "../assets/menus";

export default {
  props: {
    current_block: {
      type: String,
      default: "",
    },
    menu_visibility: {
      type: Boolean,
      default: false,
    },
  },
  data() {
    return {
      menus,
    };
  },
  methods: {
    scroll(key) {
      document.querySelector(`#${key}`).scrollIntoView({ behavior: "smooth" });
    },
  },
};
</script>
