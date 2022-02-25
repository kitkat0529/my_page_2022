<template lang="pug">
.m-auto(:class="['w-7/12']")
  .mt-10.mb-16.border-2.border-gray-300.p-7.rounded-lg.relative(
    v-for="skill in skills", data-aos="zoom-in"
  )
    .text-gray-200.font-mono.text-md.mb-2.absolute.-top-3.bg-gray-800.px-2 {{ skill.name }}
    .level.italic.text-center.text-green-500.font-mono.text-4xl.font-bold
      span {{ skill.level }}
      span.not-italic.text-gray-500.text-lg.ml-3.font-normal / 10
</template>

<script>
import skills from "../../assets/skills";

export default {
  data() {
    return {
      skills,
    };
  },
};
</script>
