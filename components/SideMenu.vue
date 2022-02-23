<template lang="pug">
ul#side-menu(v-if="current_block !== ''")
  li(v-for="menu in menus", :class="{ 'active': current_block == menu }")
    i
    span.text-gray-200.uppercase {{ menu }}
</template>

<script>
export default {
  props: {
    current_block: {
      type: String,
      default: "",
    },
  },
  data() {
    return {
      menus: ["top", "autobiography", "skill", "resume"],
    };
  },
};
</script>
