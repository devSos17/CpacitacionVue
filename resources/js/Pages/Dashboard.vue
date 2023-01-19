<template>
    <div class="container">
        <p>Hoy veremos Components</p>
    </div>
</template>

<script>
export default {
    props: {
        entradas: {
            type: Array,
            default: [],
        },
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
