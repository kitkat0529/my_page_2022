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
    span.text-gray-200 {{ menu }}
</template>

<script>
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
      menus: {
        top: "個人資料",
        autobiography: "簡歷",
        skill: "技能",
        resume: "經歷與網頁作品",
      },
    };
  },
  methods: {
    scroll(key) {
      document.querySelector(`#${key}`).scrollIntoView({ behavior: "smooth" });
    },
  },
};
</script>
