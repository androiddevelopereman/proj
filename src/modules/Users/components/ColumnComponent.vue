<script setup>
import { ref } from "vue";
import testData from "..//..//../..//data (1)";
// limit testData to 10 items
const limitedTestData = ref(testData.slice(0, 12));

const chartOptions = ref({
  chart: {
    type: "bar",
  },
  plotOptions: {
    bar: {
      borderRadius: 4,
      borderRadiusApplication: "end",
      horizontal: false,
    },
  },
  title: {
    text: "Speed Monitor",
    align: "left",
  },
  yaxis: {
    title: {
      text: "Speed",
    },
  },
  xaxis: {
    title: {
      text: "Time",
    },
  },
});
// const de= ref
const series = ref([
  {
    name: "Cool",
    data: limitedTestData.value.map((item) => ({
      x: item.last_gps_device,
      y: item.speed,
    })),
  },
]);
</script>

<template>
  <main>
    <apexchart
      width="100%"
      height="600"
      type="bar"
      :options="chartOptions"
      :series="series"
    ></apexchart>
  </main>
</template>
