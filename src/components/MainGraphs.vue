<script setup lang="ts">
import {
  Chart as ChartJS,
  Title,
  Tooltip,
  Legend,
  BarElement,
  CategoryScale,
  LinearScale
} from 'chart.js'
import { Bar } from 'vue-chartjs'

ChartJS.register(CategoryScale, LinearScale, BarElement, Title, Tooltip, Legend)

const data = {
        labels: ['January', 'February', 'March'],
        datasets: [{ data: [40, 20, 12] }]
}
      

</script>

<template>
    <h2>Chart 1</h2>
    <div class="chartContainer">
        <Bar :data="data" />
    </div>
</template>

<style scoped>
.chartContainer {
    background-color: antiquewhite;
    padding: 20px;
}
</style>