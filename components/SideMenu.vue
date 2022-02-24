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
  },
  data() {
    return {
      menu_visibility: false,
      menus: {
        top: "個人資料",
        autobiography: "簡歷",
        skill: "技能",
        resume: "經歷與網頁作品",
      },
    };
  },
  mounted() {
    window.addEventListener("scroll", this.setMenuVisibility);
  },
  methods: {
    scroll(key) {
      document.querySelector(`#${key}`).scrollIntoView({ behavior: "smooth" });
    },
    setMenuVisibility() {
      const window_offset = window.pageYOffset;
      const first_block =
        document.querySelector("#autobiography").offsetTop - 500;

      this.menu_visibility = window_offset > first_block;
    },
  },
};
</script>
