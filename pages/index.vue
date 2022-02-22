<template lang="pug">
.bg-gray-800
  .h-screen
    .index-info
      .main-section
        .information
          .picture(data-aos="zoom-out", data-aos-duration="1000")
          div
            h1.text-gray-100.text-5xl.font-mono(
              data-aos="fade-up", data-aos-duration="1000"
            ) Leah Chou
            p.text-gray-100.font-mono.text-blut-400.typewriter A Frontend Engineer
            .mt-6.font-mono
              .detail-item.text-gray-100(
                data-aos="fade-up", data-aos-delay="1000", data-aos-duration="1000"
              )
                fa(:icon="['fas', 'map-marker-alt']", :class="['ml-0.5']")
                | Taipi, Taiwan
              .detail-item.text-gray-100(
                data-aos="fade-up", data-aos-delay="1200", data-aos-duration="1000"
              )
                fa(:icon="['fas', 'envelope']")
                | leahchou.fee@gmail.com
              .mt-5.text-gray-100.text-lg(
                data-aos="fade-up", data-aos-delay="1400", data-aos-duration="1000"
              )
                template(v-for="(link, icon) in links")
                  a.mr-3(
                    :href="link",
                    :class="['hover:text-green-300']",
                    target="_blank"
                  )
                    fa(:icon="['fab', icon]")
    vue-particles.h-screen
  section#skill.h-screen(data-aos="fade-up", data-aos-duration="1000")
    h2.text-gray-100.text-5xl.font-mono.text-center Skill
    .skill-canvas
      skill-component(data-aos="zoom-in", data-aos-delay="500")
  resume-component
  side-menu(:current_block="current_block")
</template>

<script>
import SkillComponent from "../components/SkillComponent.vue";
import ResumeComponent from "../components/ResumeComponent.vue";
import SideMenu from "../components/SideMenu.vue";

export default {
  name: "IndexPage",
  components: {
    "skill-component": SkillComponent,
    "resume-component": ResumeComponent,
    "side-menu": SideMenu,
  },
  data() {
    return {
      offset: {
        skill: null,
        resume: null,
      },
      current_block: "",
      skill_visibility: false,
      links: {
        linkedin: "https://www.linkedin.com/in/leah-chou-954438199/",
        github: "https://github.com/kitkat0529",
      },
    };
  },
  mounted() {
    window.addEventListener("scroll", this.setCurrentBlock);
    this.offset.skill = document.getElementById("skill");
    this.offset.resume = document.getElementById("resume");
    this.setCurrentBlock();
  },
  methods: {
    setCurrentBlock() {
      const window_offset = window.pageYOffset;
      const skill_offset = this.offset.skill.offsetTop - 100;
      const resume_offset = this.offset.resume.offsetTop - 500;

      if (window_offset < skill_offset) {
        this.current_block = "";
      } else if (
        window_offset > skill_offset &&
        window_offset < resume_offset
      ) {
        this.current_block = "skill";
        if (!this.skill_visibility) {
          this.skill_visibility = true;
        }
      } else if (window_offset > resume_offset) {
        this.current_block = "resume";
      }
    },
  },
};
</script>
