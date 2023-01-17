<template>
    <div>
        <h1>{{ producto }}</h1>
        <p>Precio: {{ precio }}(iva16%:{{ precioCalculado }})</p>
    </div>
</template>

<script>
export default {
    data() {
        return {
            producto: "Hello world",
            precio: 100,
            iva: 1.16,
        };
    },
    methods: {
        diHola() {
            console.log("hola");
        },
    },
    computed: {
        precioCalculado() {
            console.log("se recalculo el precio");
            return this.precio * this.iva;
        },
    },
    watch: {
        precio(newVal, oldVal) {
            console.log(`se actualizo el precio de ${oldVal} a ${newVal}`);
        },
    },
};
</script>

<style>
</style>
