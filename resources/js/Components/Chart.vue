<template>
    <Bar :data="data" :options="options" />
        <Doughnut :data="data" :options="options" />
    <div>
        <pre>{{ data }}</pre>
    </div>
</template>

<script lang="ts">
import {
    Chart as ChartJS,
    Title,
    Tooltip,
    Legend,
    BarElement,
    CategoryScale,
    LinearScale,
} from "chart.js";
import { Bar, Doughnut } from "vue-chartjs";

ChartJS.register(
    CategoryScale,
    LinearScale,
    BarElement,
    Title,
    Tooltip,
    Legend
);

export default {
    components: {
        Bar,
        Doughnut,
    },
    props: {
        data: {
            type: Object,
            default:{
                labels: ["January", "February", "March"],
                datasets: [{ data: [40, 20, 12] }],
            },
            options: {
                type: Object,
                default: {
                    responsive: true,
                },
            },
        }
    }
};
</script>
