<template>
    <div class="container">
        <Chart
            :data="datosProcesados"
        />
    </div>
</template>

<script>
import Chart from "@/Components/Chart.vue";
export default {
    data(){
        return {
            labelsStaicos: ['persona', 'institucion', 'cosa'],
        }
    },
    props: {
        entradas: {
            type: Array,
            default: [],
        },
    },
    computed: {
        datosProcesados(newVal){
            let datos = { 
                labels: this.labelsStaicos,
                // datasets:[{data:[]}] 
                };
            let i = 0, data = [];
            this.labelsStaicos.forEach((label)=>{
                data[i] = this.entradas
                .filter((entrada)=> entrada.tipo == label)
                .reduce((acc,current)=> acc + current.cantidad,0)    
                i++;
            });
            datos.datasets = [{data:data}];
            console.log({datos})
            return datos;
        }
    },
    components: {
        Chart,
    },
};
</script>

<style>
.container {
    display: flex;
    text-align: center;
    justify-content: center;
    flex-direction: column;
}

.rojoGordito {
    color: red;
    padding: 50px 50px;
    border-radius: 50px;
    border-color: green;
    border-style: solid;
}
.verdeGordito {
    color: green;
    padding: 50px 50px;
    border-radius: 50px;
    border-color: red;
    border-style: dashed;
}
.margin-top {
    margin-top: 20px;
}
.margin-buttom {
    margin-top: 20px;
}
.margin-buttom {
    margin-top: 20px;
}
.sub {
    text-decoration: underline;
}
</style>
