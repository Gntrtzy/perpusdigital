<template>
    <div>
      <h1>Statistik Pengunjung</h1>
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
    'June',
  ];
  
  const data = {
    labels: labels,
    datasets: [{
      label: 'Pengunjung',
      backgroundColor: 'rgb(38, 92, 181)',
      borderColor: 'rgb(255, 99, 132)',
      data: [20, 10, 5, 2, 20, 50, 77],
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
    width: 1500px;
  }
  </style>