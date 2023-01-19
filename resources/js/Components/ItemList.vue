<template>
    <template v-if="datos">
        <div v-for="(dato, i) in datos" :key="i">
            <Item :dato="dato" @computado="bubble"/>
        </div>
    </template>
</template>

<script>
import Item from "./Item.vue";
export default {
    components: {
        Item,
    },
    props: {
        datos: [],
    },
    methods:{
        bubble(data){
            this.$emits('computado', data)
        }
    },
    emits:['computado']
};
</script>

<style></style>
