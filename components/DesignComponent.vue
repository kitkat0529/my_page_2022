<template lang="pug">
div
  section#design.min-h-screen(data-aos="fade-up", data-aos-duration="1000")
    .title.top-0.pt-8.pb-5.sticky
      h2.text-gray-100.text-4xl.font-mono.text-center.tracking-widest
        | {{ title }}
    .mt-12.mx-auto(:class="['w-8/12']")
      .grid.grid-cols-2.gap-4(
        :class="['sm:grid-cols-3', 'md:grid-cols-4']"
      )
        .image.p-1(
          v-for="(image, index) in images",
          :class="['text-red-100']"
          :style="{ 'background-image': `url(${image.path})` }",
          @click="select(index)"
        )
  #lightbox.w-screen.h-screen.fixed.top-0(v-if="selected !== null")
    .content.m-auto.max-w-xl.relative
      .close.absolute.-top-14.right-5.p-2.cursor-pointer(
        :class="['sm:top-0']"
      )
        fa.text-3xl.text-gray-500(
          :icon="['fa', 'times']",
          :class="['hover:text-gray-100']"
          @click="selected = null"
        )
      .next-button.p-2.cursor-pointer(:class="['sm:p-2', 'md:p-4']", @click="next(-1)")
        fa.text-4xl.text-gray-500(
          :icon="['fa', 'angle-left']",
          :class="['hover:text-gray-100']"
        )
      .display-image
        img(:src="images[selected].path")
        .page.text-gray-500.text-sm(:class="['sm:text-xs']")
          | {{ selected + 1 }} / {{ images.length }}
      .next-button.p-2.cursor-pointer(:class="['sm:p-2', 'md:p-4']", @click="next(1)")
        fa.text-4xl.text-gray-500(
          :icon="['fa', 'angle-right']",
          :class="['hover:text-gray-100']"
        )

    .w-screen.h-screen.absolute.top-0(@click="selected = null")
</template>

<script>
import images from "../assets/design_images";
export default {
  props: {
    title: {
      type: String,
      default: "",
    },
  },
  data() {
    return {
      selected: null,
      images,
    };
  },
  watch: {
    selected(value) {
      if (value === null) {
        document.body.style.overflow = "auto";
      }
    },
  },
  mounted() {
    document.addEventListener("keydown", this.keydownCallback);
  },
  methods: {
    select(index) {
      this.selected = index;
      document.body.style.overflow = "hidden";
    },
    next(value) {
      if (this.selected === null) {
        return;
      }
      const new_selected = this.selected + value;
      if (new_selected < 0) {
        this.selected = this.images.length - 1;
      } else if (new_selected === this.images.length) {
        this.selected = 0;
      } else {
        this.selected = new_selected;
      }
    },
    keydownCallback(element) {
      switch (element.keyCode) {
        case 37:
          this.next(-1);
          break;
        case 39:
          this.next(1);
          break;
      }
    },
  },
};
</script>
