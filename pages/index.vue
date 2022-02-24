<template lang="pug">
.bg-gray-800
  #top.h-screen
    .index-info
      .main-section
        .information.grid.grid-cols-1.mt-36(
          :class="['md:grid-cols-2', 'lg:grid-cols-3', 'xl:grid-cols-4', 'md:mt-80']"
        )
          .picture(data-aos="zoom-out", data-aos-duration="1000")
          .mt-5(:class="['md:mt-0']")
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
  autobiography-component
  section#skill.min-h-screen(data-aos="fade-up", data-aos-duration="1000")
    h2.text-gray-100.text-5xl.font-mono.text-center.tracking-widest 技能
    .skill-canvas
      skill-component(data-aos="zoom-in", data-aos-delay="500")
  resume-component
  .p-5
  side-menu(:current_block="current_block", :menu_visibility="menu_visibility")
  mobile-menu(:current_block="current_block", :button_visibility="menu_visibility")
</template>

<script>
import AutobiographyComponent from "../components/AutobiographyComponent.vue";
import SkillComponent from "../components/SkillComponent.vue";
import ResumeComponent from "../components/ResumeComponent.vue";
import SideMenu from "../components/SideMenu.vue";
import MobileMenu from "../components/mobile/SideMenu.vue";

export default {
  name: "IndexPage",
  components: {
    "autobiography-component": AutobiographyComponent,
    "skill-component": SkillComponent,
    "resume-component": ResumeComponent,
    "side-menu": SideMenu,
    "mobile-menu": MobileMenu,
  },
  data() {
    return {
      offset: {
        autobiography: null,
        skill: null,
        resume: null,
      },
      current_block: "",
      skill_visibility: false,
      links: {
        linkedin: "https://www.linkedin.com/in/leah-chou-954438199/",
        github: "https://github.com/kitkat0529",
      },
      menu_visibility: false,
    };
  },
  mounted() {
    window.addEventListener("scroll", this.setCurrentBlock);
    Object.keys(this.offset).forEach((key) => {
      this.offset[key] = document.getElementById(key);
    });
    this.setCurrentBlock();
  },
  methods: {
    setCurrentBlock() {
      const window_offset = window.pageYOffset;
      const autobiography_offset = this.offset.autobiography.offsetTop - 500;
      const skill_offset = this.offset.skill.offsetTop - 300;
      const resume_offset = this.offset.resume.offsetTop - 300;

      this.menu_visibility = window_offset > autobiography_offset;

      if (window_offset < autobiography_offset) {
        this.current_block = "";
      } else if (
        window_offset > autobiography_offset &&
        window_offset < skill_offset
      ) {
        this.current_block = "autobiography";
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
