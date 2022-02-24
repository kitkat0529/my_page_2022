<template lang="pug">
  #mobile-menu.fixed.right-20.cursor-pointer.block.menu-nav(
    :class="['md:hidden', {'active': menu_visibility}, {'show': button_visibility}]"
  )
    a(
      v-for="(menu, key) in menus"
      @click="scroll(key)"
    )
      fa.text-2xl(
        :icon="['fa', menu]",
        :class="[ current_block === key ? 'text-green-500' : 'text-green-900' ]"
      )
    .toggle.rounded-full.absolute.p-7(
      @click="menu_visibility = !menu_visibility",
      :class="[ \menu_visibility ? \
        'bg-green-700 hover:bg-green-900' \
        : 'bg-green-300 hover:bg-green-500' \
      ]"
    )
      span
      span
      span
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
      button_visibility: false,
      menu_visibility: false,
      menus: {
        top: "user",
        autobiography: "file",
        skill: "hammer",
        resume: "folder",
      },
    };
  },
  mounted() {
    window.addEventListener("scroll", this.setButtonVisibility);
  },
  methods: {
    scroll(key) {
      switch (key) {
        case "top":
          this.menu_visibility = false;
      }
      document.querySelector(`#${key}`).scrollIntoView({ behavior: "smooth" });
    },
    setButtonVisibility() {
      const window_offset = window.pageYOffset;
      const first_block =
        document.querySelector("#autobiography").offsetTop - 500;

      this.button_visibility = window_offset > first_block;
      if (window_offset < first_block) {
        this.menu_visibility = false;
      }
    },
  },
};
</script>
