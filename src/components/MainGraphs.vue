<script setup lang="ts">
import { ref} from 'vue'
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

const chartData = ref({
    labels: ['1960s', '1970s', '1980s', '1990s', '2000s', '2010s'],
    datasets: [
    {
      label: 'Number of Births in UK in mln',
      data: [7.2, 7.3, 6.7, 6.7, 6.8, 6.4],
      backgroundColor: [
        'rgba(255, 99, 132, 0.5)', 
        'rgba(54, 162, 235, 0.5)', 
        'rgba(255, 206, 86, 0.5)', 
        'rgba(75, 192, 192, 0.5)', 
        'rgba(153, 102, 255, 0.5)', 
        'rgba(255, 159, 64, 0.5)' 
      ]
    }
  ]
})

const chartOptions = ref({
  responsive: true
})
      
</script>

<template>
    <h2>Chart 1</h2>
    <div class="chartContainer">
        <Bar
            :options="chartOptions"
            :data="chartData"
        />
    </div>
</template>

<style scoped>
.chartContainer {
    background-color: rgb(246, 239, 229);
    padding: 20px;
    border-radius: 10px;
    border: 3px solid black;
}
</style>