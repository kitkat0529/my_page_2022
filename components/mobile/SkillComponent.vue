<template lang="pug">
.m-auto(:class="['w-9/12']")
  .my-10(v-for="skill in skills", data-aos="zoom-in")
    .text-gray-200.font-mono.text-md.mb-2 - {{ skill.name }}
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
