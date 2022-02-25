<script>
import { Radar } from "vue-chartjs";
import skills from "../assets/skills";

export default {
  extends: Radar,
  data() {
    const main_color = "#6ee7b7ba";
    const background_color = "#202a37";
    return {
      data: {
        labels: Object.values(skills).map((skill) => skill.name),
        datasets: [
          {
            label: "Skill Level",
            backgroundColor: main_color,
            borderColor: main_color,
            data: Object.values(skills).map((skill) => skill.level),
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
            fontSize: 12,
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
