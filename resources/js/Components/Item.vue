<template>
    <div class="item">
        <slot/>
        <slot v-if="dato" name="dataZone" :data="dato">
            <p>Esto es Contenido por default</p>
            <pre>{{ dato }}</pre>
        </slot>
        <button @click="emiteEvento(dato)">Emite</button>
    </div>
</template>

<script>
export default {
    props: {
        dato: {},
    },
    methods: {
        emiteEvento(dato){
            this.$emit('computado',dato)
        }
    },
    emits:['computado']
};
</script>

<style scoped>
div {
    background-color: greenyellow;
}
.item {
    display: block;
    border: 1px solid;
    padding: 1.5em;
    margin: 10px;
}
</style>
