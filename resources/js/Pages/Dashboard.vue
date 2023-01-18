<template>
    <div v-for="(entradas, indice) of entradas" :key="indice">
        <p>{{indice}}:{{entradas}}</p>
    </div>
</template>

<script>
export default {
    data() {
        return {
            objeto: {
                'primera_llave': 1,
                segundaLLave: "algo",
                'tercera': 1.0,
            }
        };
    },
    props:{
        entradas: {
            type: Array,
            default: [],
        },
    },
    methods: {},
    computed: {},
    watch: {},
};
</script>

<style>
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
