<template lang="pug">
  #mobile-menu.fixed.right-20.cursor-pointer.block.menu-nav(
    :class="['md:hidden', {'active': menu_visibility}, {'show': button_visibility}]"
  )
    a(
      v-for="(menu, key) in menus"
      @click="scroll(key)"
    )
      fa.text-xl(
        :icon="['fa', menu.icon]",
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
import menus from "../../assets/menus";

export default {
  props: {
    current_block: {
      type: String,
      default: "",
    },
    button_visibility: {
      type: Boolean,
      default: false,
    },
  },
  data() {
    return {
      menu_visibility: false,
      menus,
    };
  },
  watch: {
    button_visibility(current) {
      if (!current) this.menu_visibility = false;
    },
  },
  methods: {
    scroll(key) {
      switch (key) {
        case "top":
          this.menu_visibility = false;
      }
      document.querySelector(`#${key}`).scrollIntoView({ behavior: "smooth" });
    },
  },
};
</script>
