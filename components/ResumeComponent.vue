<template lang="pug">
section#resume
  h2.text-gray-100.text-5xl.font-mono.text-center.tracking-widest 經歷與網頁作品
  .mx-auto.mt-20(:class="['w-11/12', 'md:w-2/3']")
    .relative.border-l-4.border-gray-500.px-5.pb-10(
      v-for="data in informations",
      :class="['md:px-10']",
      data-aos="fade-up",
      data-aos-duration="1500",
      data-aos-delay="300"
    )
      .absolute.rounded-full.p-2.bg-gray-500.top-2(
        v-if="data.time", :class="['-left-2.5']"
      )
      .text-gray-500.text-lg.font-mono {{ data.time }}
      .text-gray-100.text-2xl {{ data.title }}
      .mt-3(v-if="data.projects && data.projects.length > 0")
        carousel(:perPage="1", :autoplay="true", :autoplayTimeout="4000")
          slide.px-2(v-for="project in data.projects", :key="project.name")
            .p-5.rounded.bg-gray-600.w-full.overflow-hidden
              div
                .text-gray-100.text-xl.font-mono.font-bold.tracking-wide
                  | {{ project.name }}
                  a.text-gray-300.text-base.ml-2(
                    v-if="project.url",
                    :class="['hover:text-blue-500']",
                    :href="project.url",
                    target="_blank"
                  )
                    fa(:icon="['fa', 'link']")
                  a.text-gray-300.text-base.ml-2(
                    v-if="project.source",
                    :class="['hover:text-blue-500']",
                    :href="project.source",
                    target="_blank"
                  )
                    fa(:icon="['fab', 'github']")
                .text-gray-300.text-sm {{ project.description }}
              img.w-full.my-2(:src="project.image")
              ul(v-if="project.details && project.details.length")
                li.font-mono.text-sm.text-gray-100(v-for="detail in project.details") - {{ detail }}
</template>

<script>
import informations from "../assets/informations";

export default {
  data() {
    return {
      informations,
    };
  },
};
</script>
