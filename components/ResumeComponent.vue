<template lang="pug">
section#resume
  h2.text-gray-100.text-5xl.font-mono.text-center.tracking-widest 經歷與網頁作品
  .mx-auto.mt-20(:class="['w-11/12', 'md:w-2/3']")
    .relative.border-l-4.border-gray-500.px-5.pb-10(
      v-for="data in informations",
      :class="['md:px-10']",
      data-aos="fade-up",
      data-aos-duration="2000",
      data-aos-delay="500"
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
export default {
  data() {
    return {
      informations: [
        {
          time: "2021.11 - Now",
          title: "個人專案",
          projects: [
            {
              name: "Palantirrrrr",
              description: "公司關係搜尋網站",
              details: ["D3 network graph", "Nuxt.js"],
              url: "",
              source: "",
              image:
                "https://images.cakeresume.com/JLOBP/leah-chou-fd6c52/dc810106-f743-453f-b25f-84d30c213cb7.png",
            },
            {
              name: "My Page",
              description: "個人履歷頁面",
              details: ["內容規劃與頁面設計", "Nuxt.js"],
              url: "https://leahchou-resume.herokuapp.com/",
              source: "https://github.com/kitkat0529/my_page_2022",
              image:
                "https://images.cakeresume.com/JLOBP/leah-chou-fd6c52/5cc22d16-4721-4119-9b29-669260c455c6.png",
            },
          ],
        },
        {
          time: "2020.05 - 2021.11",
          title: "源動力有限公司",
          projects: [
            {
              name: "Beestore",
              description: "網店架設系統",
              details: [
                "第一版為Laravel + Vue 2",
                "第二版為Vue 3",
                "前後台會員系統",
                "購物車結帳系統",
                "多國語言顯示(i18n)",
              ],
              url: "",
              source: "",
              image:
                "https://images.cakeresume.com/JLOBP/leah-chou-fd6c52/20f7988b-dc63-4ed1-b579-e2c9ad5016b1.png",
            },
          ],
        },
        {
          time: "",
          title: "個人專案",
          projects: [
            {
              name: "RPG Bar",
              description: "RPG風格酒吧網站（虛構）",
              details: ["Nuxt.js", "素材製作、內容規劃與頁面設計"],
              url: "https://rpg-bar.herokuapp.com/",
              source: "",
              image:
                "https://images.cakeresume.com/JLOBP/leah-chou-fd6c52/9e5781c0-80cf-4fd2-9fd2-559ab46416ec.png",
            },
          ],
        },
        {
          time: "2019.05 - 2020.05",
          title: "駭音科技有限公司",
          projects: [
            {
              name: "HC Music",
              description: "品牌官方網站",
              details: ["純HTML + CSS", "頁面設計"],
              url: "https://thehcmusic.com/",
              source: "",
              image:
                "https://images.cakeresume.com/JLOBP/leah-chou-fd6c52/5e80c8c5-a07c-4b22-9473-3f122176e5e2.png",
            },
            {
              name: "MamiYoga",
              description: "瑜伽線上課程網站",
              details: ["Nuxt.js", "多國語言顯示(i18n)"],
              // url: "https://mamiyoga.ludonow.com/",
              source: "",
              image:
                "https://images.cakeresume.com/JLOBP/leah-chou-fd6c52/8e633053-e0fa-4f13-bb36-cb7ed7a2a3e0.png",
            },
            {
              name: "Ludo BMI",
              description: "BMI/TDEE試算網站",
              details: ["BMI計算機", "Vue 2"],
              // url: "https://mamiyoga.ludonow.com/bmi",
              source: "",
              image:
                "https://images.cakeresume.com/JLOBP/leah-chou-fd6c52/0137f8dc-b26e-44e9-9369-7588113e82fe.png",
            },
            {
              name: "祈初托嬰",
              description: "幼兒園網站",
              details: ["Vue 2", "百度地圖顯示"],
              // url: "http://www.kidchoo.com/",
              source: "",
              image:
                "https://images.cakeresume.com/JLOBP/leah-chou-fd6c52/3896949e-6421-4c4a-a316-2f05c195afe2.png",
            },
          ],
        },
        {
          time: "2019",
          title: "個人專案",
          projects: [
            {
              name: "究極逃出",
              description: "密室逃脫企劃網站（虛構）",
              details: ["純HTML + CSS", "素材製作、內容規劃與頁面設計"],
              url: "https://kitkat0529.github.io/",
              source: "https://github.com/kitkat0529/kitkat0529.github.io",
              image:
                "https://images.cakeresume.com/JLOBP/leah-chou-fd6c52/420a61ce-f6de-409d-bc2d-613abe2c44d0.png",
            },
            {
              name: "軟綿綿",
              description: "樂團網站",
              details: ["純HTML + CSS", "素材製作、內容規劃與頁面設計"],
              url: "http://tutorial.jumpdesign.tw/portfolio/w_66/index.html#firstPage",
              source: "https://github.com/kitkat0529/sofutoooooo",
              image:
                "https://images.cakeresume.com/JLOBP/leah-chou-fd6c52/4bc8378a-4f6b-409e-b4d7-fc8d868f4a96.png",
            },
          ],
        },
      ],
    };
  },
};
</script>
