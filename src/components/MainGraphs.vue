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

const birthsUKData = ref({
    labels: ['1960s', '1970s', '1980s', '1990s', '2000s', '2010s'],
    datasets: [
    {
      label: 'Number of Births in UK in mln',
      data: [7.2, 7.3, 6.7, 6.7, 6.8, 6.4],
      backgroundColor: [
        '#6643b5', 
        '#f0d43a', 
        '#8594e4', 
        '#ff7e67', 
        '#42b883', 
        '#eb2632' 
      ]
    }
  ]
})

const birthsWorldData = ref({
    labels: ['1960s', '1970s', '1980s', '1990s', '2000s', '2010s'],
    datasets: [
    {
    label: 'Number of Births Worldwide in mln',
      data: [91.3, 103.7, 109.3, 116.4, 120.9, 133.4], 
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

const deathsUKData = ref({
  labels: ['1960s', '1970s', '1980s', '1990s', '2000s', '2010s'],
  datasets: [
    {
      label: 'Number of Deaths in UK in mln',
      data: [0.7, 0.8, 0.9, 1.0, 1.1, 1.2], 
      backgroundColor: [
        '#79c2d0', 
        '#53a8b6', 
        '#5585b5', 
        '#00bbf0', 
        '#005792', 
        '#00204a' 
      ]
    }
  ]
})

const deathsWorldData = ref({
  labels: ['1960s', '1970s', '1980s', '1990s', '2000s', '2010s'],
  datasets: [
    {
      label: 'Number of Deaths Worldwide in mln',
      data: [33.9, 36.5, 39.5, 43.5, 48.1, 55.3], 
      backgroundColor: [
        '#ffc93c', 
        '#ff9a3c', 
        '#ff6f3c', 
        '#f95959', 
        '#c3195d', 
        '#680747' 
      ]
    }
  ]
})

const chartOptions = ref({
  responsive: true
})   

const title = ref(0);
const titles = ['Births in UK', 'Births in the world','Deaths in UK', 'Deaths in the world'];
const data = [birthsUKData, birthsWorldData, deathsUKData, deathsWorldData];

const handleGraph = () => {
   if (title.value < titles.length - 1) title.value++;
   else title.value = 0;
}
</script>

<template>
    <div>
        <h2>{{ titles[title] }}</h2>
        <button @click="handleGraph" >Next</button>
    </div>

    <div class="chartContainer">
        <Bar
            :options="chartOptions"
            :data="data[title].value"
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