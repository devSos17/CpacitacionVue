# Capacitacion en VuejS

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

## Glosario

### DOM

> Document Object Model

Es el mecanimso por el cual podemos intercatuar con el html de una pagina
a traves de javascript

---

Vue Inyecta su codigo "template" dentro del DOM.

---
