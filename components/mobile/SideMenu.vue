<template lang="pug">
  #mobile-menu.fixed.right-20.bottom-20.cursor-pointer.block(
    v-if="current_block && current_block !== 'top'"
    :class="[ menu_visibility ? 'active' : '', 'md:hidden' ]"
  )
    a(
      v-for="(menu, key) in menus"
      @click="scroll(key)"
    )
      fa.text-2xl(
        :icon="['fa', menu]",
        :class="[ current_block === key ? 'text-green-900' : 'text-green-500' ]"
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
      menu_visibility: false,
      menus: {
        top: "user",
        autobiography: "file",
        skill: "hammer",
        resume: "folder",
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
