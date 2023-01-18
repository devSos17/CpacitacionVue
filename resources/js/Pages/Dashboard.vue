<template>
    <div>
        <form action="" @submit.prevent.stop="save">
            <!-- <input type="text" v-model="form.nombre" /> -->
            <input type="checkbox" v-model="visible" />
            <pre>{{ texto }}</pre>
            <button type="submit">Borrar</button>
        </form>
    </div>
</template>

<script>
import { useForm } from "@inertiajs/vue3";
export default {
    data() {
        return {
            visible: true,
            texto: "",
            selected: false,
            okay: false,
            margins: "margin-buttom margin-top",
            claseActiva: "rojoGordito",
            decorador: "sub",
            form: useForm({
                nombre: "",
            }),
        };
    },
    methods: {
        save() {
            // console.log({ form: this.form });
            this.form.post(route('capPost'));
        },
    },
    computed: {},
    watch: {
        visible(newVal, oldVal){
            if(!oldVal && newVal) console.log("paso de falso a verdadero") 
        }
    },
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
