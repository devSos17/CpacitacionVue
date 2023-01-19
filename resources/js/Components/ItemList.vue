<template>
    <template v-if="datos">
        <div v-for="(dato, i) in datos" :key="i">
            <Item :dato="dato" />
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
};
</script>

<style></style>
