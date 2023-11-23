<script setup>
import { onMounted } from 'vue';
import Chart from 'chart.js/auto';

onMounted(()=>{
    const ctx = document.getElementById('life');

    const labels = ["lundi",'mardi',"mercredi","jeudi","vendredi","samedi","dimanche"];
    const data = {
    labels: labels,
    datasets: [{
        label: 'My First Dataset',
        data: [65, 59, 80, 81, 56, 55, 40],
        fill: false,
        borderColor: 'rgb(75, 192, 192)',
        tension: 0.1
    }]
    };

    new Chart(ctx, {
    type: 'line',
    data: data
    });
    const _ctx = document.getElementById('stats');

    const _data = {
    labels: [
        'Eating',
        'Drinking',
        'Sleeping',
        'Designing',
        'Coding',
        'Cycling',
        'Running'
    ],
    datasets: [{
        label: 'My First Dataset',
        data: [65, 59, 90, 81, 56, 55, 40],
        fill: true,
        backgroundColor: 'rgba(255, 99, 132, 0.2)',
        borderColor: 'rgb(255, 99, 132)',
        pointBackgroundColor: 'rgb(255, 99, 132)',
        pointBorderColor: '#fff',
        pointHoverBackgroundColor: '#fff',
        pointHoverBorderColor: 'rgb(255, 99, 132)'
    }, {
        label: 'My Second Dataset',
        data: [28, 48, 40, 19, 96, 27, 100],
        fill: true,
        backgroundColor: 'rgba(54, 162, 235, 0.2)',
        borderColor: 'rgb(54, 162, 235)',
        pointBackgroundColor: 'rgb(54, 162, 235)',
        pointBorderColor: '#fff',
        pointHoverBackgroundColor: '#fff',
        pointHoverBorderColor: 'rgb(54, 162, 235)'
    }]
    };

    const config = {
    type: 'radar',
    data: _data,
    options: {
        elements: {
        line: {
            borderWidth: 3
        }
        }
    },
    };

    new Chart(_ctx, config);
});
</script>

<template>
<div class="p-5 h-screen flex flex-col gap-3">
    <div class="skeleton h-[10vh] w-full grid grid-cols-3 justify-center place-items-center gap-5">
        <div class="flex gap-3 w-full pl-5 pr-5">
            <select class="select select-primary w-full max-w-xs">
                <option disabled selected>Server</option>
                <option>All</option>
                <option>http://127.0.0.0:4700</option>
                <option>http://127.0.0.0:4600</option>
                <option>http://127.0.0.0:4500</option>
            </select>

            <select class="select select-primary w-full max-w-xs">
                <option disabled selected>Rounds</option>
                <option>All</option>
                <option>Rounds 1</option>
                <option>Rounds 2</option>
                <option>Rounds 3</option>
            </select>
        </div>
    
        <input type="text" placeholder="https://127.0.0.0:1256" class="input input-bordered w-full max-w-xs" disabled/>

        <div class="flex gap-3 w-full justify-end p-5">
            <div class="indicator pr-5 pl-5">
                <span class="indicator-item badge badge-secondary"></span> 
                <div class="bg-base-300 flex gap-2">
                    <span>Waiting</span>
                    <span class="loading loading-dots loading-xs"></span>
                </div>
            </div>
            <label class="flex cursor-pointer gap-2">
                <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="5"/><path d="M12 1v2M12 21v2M4.2 4.2l1.4 1.4M18.4 18.4l1.4 1.4M1 12h2M21 12h2M4.2 19.8l1.4-1.4M18.4 5.6l1.4-1.4"/></svg>
                <input type="checkbox" value="dark" class="toggle theme-controller"/>
                <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M21 12.79A9 9 0 1 1 11.21 3 7 7 0 0 0 21 12.79z"></path></svg>
              </label>
        </div>
        
    </div>
    <div class="flex grow h-full w-full gap-3">
        <div class="skeleton h-full w-[20%]">
            
        </div>
        <div class="skeleton h-full grow grid grid-cols-2 gap-3 p-3">
            <div class="mockup-code h-full w-full"></div>
            <div class="h-full w-full grid grid-rows-2 gap-3">
                <div class="w-full h-full flex justify-center">
                    <canvas id="life"></canvas>
                </div>
                <div class="w-full h-full">
                    <canvas id="stats"></canvas>
                </div>
            </div>
        </div>
    </div>
  </div>


</template> 