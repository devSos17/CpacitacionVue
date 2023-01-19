<template>
    <div class="item">
        <slot />
        <slot v-if="dato" name="dataZone" :data="dato">
            <p>Esto es Contenido por default</p>
            <pre>{{ dato }}</pre>
        </slot>
    </div>
</template>

<script>
export default {
    props: {
        dato: {},
    },
};
</script>

<style scoped>
.item::v-deep {
    display: block;
    border: 1px solid;
    padding: 1.5em;
    margin: 10px;
}
</style>
