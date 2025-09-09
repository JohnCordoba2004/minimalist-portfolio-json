<template>
  <div style="max-width: 500px; margin: auto; ">
    <canvas id='chart-roles' width='500' height="300"></canvas>
  </div>
</template>

<script setup>
import { onMounted } from 'vue';
import Chart from 'chart.js/auto';

onMounted(() => {
  console.log("✅ Montando chart...");
  const ctx = document.getElementById('chart-roles')?.getContext('2d')

  if (!ctx) {
    console.warn("⚠️ No se encontro el canvas");
    return;
  }

  new Chart(ctx, {
    type: 'bar',
    data: {
      labels: ['Frontend', 'Backend', 'Fullstack'],
      datasets: [
        {
          label: 'Proyectos',
          data: [5, 2, 3],
          backgroundColor: ["#4ade80", "#60a5fa", "#f472b6"]
        }
      ]
    },
    options: {
      responsive: true,
      maintainAspectRatio: false, // 👈 clave para que respete el tamaño del contenedor
      plugins: {
        legend: { display: true }
      }
    }
  })
})
</script>
