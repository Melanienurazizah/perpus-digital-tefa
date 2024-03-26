<template>
    <div>
        <canvas id="myChart"></canvas>
    </div>
</template>

<script setup>
import Chart  from 'chart.js/auto';

const labels=[
    'january',
    'february',
    'march',
    'april',
    'may',
    'june',
];

const data= {
    labels :labels,
    datasets:[{
        label:'Pengunjung',
        backgroundColor:'rgb(211, 211, 211)',
        borderColor:'rgb(255, 99, 132)',
        data:[10,18,20,15,15,24,45],
    }]
};

const config = {
    type:'bar',
    data:data,
    options:{}
};

onMounted(()=>{
    const myChart = new Chart(
    document.getElementById('myChart'),
    config
);
})
</script>