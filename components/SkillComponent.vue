<script>
import { Radar } from "vue-chartjs";

export default {
  extends: Radar,
  data() {
    const main_color = "#6ee7b7ba";
    const background_color = "#202a37";
    return {
      data: {
        labels: [
          "Javascript",
          "HTML / CSS",
          "Vue",
          "Laravel",
          "Adobe Photoshop",
          "Adobe illustrator",
          "Adobe XD / Figma",
        ],
        datasets: [
          {
            label: "Skill Level",
            backgroundColor: main_color,
            borderColor: main_color,
            data: [7, 7, 6, 4, 8, 7, 5],
          },
        ],
      },
      options: {
        responsive: true,
        maintainAspectRatio: false,
        legend: {
          display: false,
        },
        scale: {
          ticks: {
            beginAtZero: true,
            max: 10,
            backdropColor: background_color,
            backgroundColor: main_color,
          },
          gridLines: {
            color: "#f3f4f630",
          },
          pointLabels: {
            fontColor: "#fff",
            fontSize: 15,
          },
          height: 600,
        },
        tooltips: {
          callbacks: {
            title: (item, data) => data.labels[item[0].index],
          },
        },
      },
    };
  },
  mounted() {
    this.renderChart(this.data, this.options);
  },
};
</script>
