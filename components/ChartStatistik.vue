<template>
    <div>
      <canvas id="myChart"></canvas>
    </div>
  </template>
  
  <script setup lang="ts">
import Chart, { type ChartConfiguration, type ChartItem } from 'chart.js/auto';
  
  const labels = [
    'January',
    'February',
    'March',
    'April',
    'May',
    'june',
    'july'
  ];
  
  const data = {
    labels: labels,
    datasets: [{
      label: 'Pengunjung',
      backgroundColor: ' #5b89ff',
      data: [2, 5, 5, 10, 5,7,3],
    }]
  };
  
  const config: ChartConfiguration = {
    type: 'bar',
    data: data,
    options: {}
  };
  
  onMounted(() => {
    const canvasTag = <ChartItem>document.getElementById('myChart')
    new Chart(
      canvasTag,
      config
    );
  })
  </script>
  
  <style scoped>
  #myChart {
    width: 1200px;
  }
  </style>