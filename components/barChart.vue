<script>
  import { Bar } from "vue-chartjs";

  export default {
    extends: Bar,
    props: ["data",
      "options",
      "height",
      "width",
      
    ],
    mounted() {
      this.renderChart(this.data, this.options);
    },
  };

</script>
