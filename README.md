# Capacitación en VuejS

## Instalar Laravel

[Documentacion de laravel](https://laravel.com/docs/9.x)

> req:
> tener php y composer instalado (laragon)
> Instalar nodejs para npm con VuejS

_Crear el proyecto_

```
composer create-project laravel/laravel <nombre-del-proyecto>
```

### Continuar con Jetstream

Depues de instalar laravel podemos intalar jetstream que configurara "Laravel Fortiy"
y Vue para brindarnos una aplicacion con el frontend end en vue y con autenticacion
preconfigurada.

```
composer require laravel/jetstream
```

Al terminar es necesario crear el projecto de jetstream

```
php artisan jetstream:install inertia
```

Esto instalar Vue y configurara Vite (Podemos saltarnos esos pasos)

```
npm install
```

Se puede continuar en la seccion de Iniciar Servidor

## Instalar sail (opcional require Docker)

Como parte de las herramientas de desarrollo laravel tiene una utilidad
para correr toda la aplicacion dentro de docker con un unico script

la forma de instalarlo es

```
php artisan sail:install
```

Donde nos dará a escoger que servicios utilizaremos.

## Configurar vite (Sin jetstream)

Como utulizaremos vue, es ideal preparar laravel para usar inertia.

Dentro de la configuracion de vite [vite.config.js]
debemos borrar el entrypoint de css y agregarlo al app.js

vite.config.js

```{js}
import { defineConfig } from "vite";
import laravel from "laravel-vite-plugin";

export default defineConfig({
    plugins: [
        laravel({
            input: ["resources/js/app.js"],
            refresh: true,
        }),
    ],
});
```

/resources/js/app.js

```{js}
import './bootstrap';
import '../css/app.css';
```

### Instalar Vue (Sin jetstream)

Instalamos vue

```
npm i vue vue-loader @vitejs/plugin-vue
```

Actualizamos los plugins dentro de vite.config.js

```
import vue from '@vitejs/plugin-vue'
...
plugins: [
    vue({
        template: {
            transformAssetUrls: {
                base: null,
                includeAbsolute: false,
            },
        },
    }),
    ...
```

# Iniciar el Servidor

---

De usar sail se usa el comando ya crae el servidor y la base de datos

```
./vendor/bin/sail up
```

---

Construir los componentes base

```
npm run build
```

Ejecutar las migraciones de la base de datos

```
php artisan migrate
```

Generar nuestra llave de cifrado

```
php artisan key:generate
```

Para ejecutar nuestro servidor de desarrollo tenemos que prender 2 servicios

Artisan para que prenda el servidor web

```
php artisan serve
```

Vite para que "renderice" nuestra pagina en tiempo real

```
npm run dev
```

## Extensiones Recomendadas

-   Dev-tools

    ![Dev-tools](./.doc.assets/dev-tools.png)
    [Link dev-tools](https://devtools.vuejs.org/)

-   Vetur

    ![Vetur](./.doc.assets/vetur.png)
    [Link dev-tools](https://devtools.vuejs.org/)

# VUE3

## Temario

-   Estructura
-   Data
-   Metodos (Mehtods)
-   Computed
-   Watchers
-   Condicionales
-   v-model
-   Eventos
-   listas (ciclos)

## Estructura

Todos los componentes de Vue pueden tener 3 areas principales

```{Vue}
<template>
// Aqui va Html
</template>

<script>
export default {
    // Aqui va javascript
};
</script>

<style>
// Aqui va CSS
</style>
```

## Data

La primer parte de cualquier Componente es los datos que maneja: sus Variables

```{Vue}
...
<script>
export default {
    data() {
        return {
            var1: 'valor1',
            ...
        }
    },
};
</script>
...
```

Esta data la podemos usar dentro de nuestro componente por medio de la "interpolación"
dentro del "template" o a través de la palabra "this[^1: En options API]" dentro de nuestro script

```{Vue}
<template>
    <h1>{{ var1 }}</h1>
</template>
<script>
export default {
    data() {
        return {
            var1: 'valor1',
        }
    },
};
</script>
...
```

## Metodos

Dentro de la logica de nuestro componente necesitmaos definir acciones (metodos)

```{Vue}
...
<script>
export default {
    ...
    methods: {
        dameAlgo() {
            // Este metodo nos regresa el valor de var1
            // y le agrega un "algo al final"
            return this.var1 + "algo";
        }
    },
};
</script>
...
```

## Computed

Vue nos permite usar un tipo especial de metodo para tener "variables"
que cambien dinamicamente despues de ser calculados.

```{Vue}
<template>
    <h1>El valor de {{ var1 }} es:{{ var2 }}</h1>
</template>
<script>
export default {
    data() {
        return {
            var1: 'valor1',
            valor: 2,
            tasa: 1.16,
        }
    },
    computed: {
        var2() {
            return this.valor * this.tasa;
        }
    },
};
</script>
...
```

## Watchers

Como parte de la reactividad de vue nos permite hacer "observadores" que esten
vigilando el estado de nuestras variables

```{Vue}
<template>
    <h1>Hola {{ nombreCompleto }}</h1>
</template>
<script>
export default {
    data() {
        return {
            nombre: 'Santiago',
            apellido: "Orozco",
        }
    },
    computed: {
        nombreCompleto() {
            return `${this.nombre} ${this.apellido}`
        }
    },
    watch: {
        nombreCompleto(newVal, oldVal) {
            console.log({newVal, oldVal})
            alert(newVal)
        }
    }
};
</script>
...
```
