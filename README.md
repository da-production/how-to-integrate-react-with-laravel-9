# <p align="center">how to integrate react with laravel 9</p>
<p align="center">
<a href="https://reactjs.org/" target="_blank">
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/a/a7/React-icon.svg/1200px-React-icon.svg.png" width="150">
</a>
<a href="https://laravel.com" target="_blank">
<img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="400">
</a>
</p>
<p align="center">In this short blog, You will learn How to Install React in Laravel 9 with Vite.</p>
<hr />

### Step 1: Install NPM Dependencies
Run the following command to install frontend dependencies:
```
npm install
```

### Step 2: Install React
Now after installing node modules we need to install reactjs in our application, for that execute the following command in the terminal npm install react@latest react-dom@latest. It will install latest version of reactjs and react-dom also. we’ll use it in jsx file.
```
npm install react@latest react-dom@latest
```

### Step 3: Install vite laravel plugin
Run the following command to install frontend dependencies:
```
npm install vite laravel-vite-plugin --save-dev
```

Step 4: Install vitejs/plugin-react plugin
n laravel 9 latest release install vitejs/plugin-react plugin for installing reactjs in laravel. This plugin provides required dependencies to run the reactjs application on vite. Vite is a  build command that bundles your code with Rollup and it runs on localhost:3000 port to give hot refresh feature.
```
npm i @vitejs/plugin-react --force
npm i @vitejs/plugin-react-refresh --force
```
Step 5: Update vite.config.js file
The latest 9.19 Provides a vite.config.js file in the root of the application to configure front-end assets preset import plugin-react and add react() to the plugins array in the defineConfig() function.
and don't forget to add proxy to vite.config.js to use it in ajax call with axios or another lib
```
import { defineConfig } from 'vite';
import laravel from 'laravel-vite-plugin';
import react from '@vitejs/plugin-react';

export default defineConfig({
    server:{
        proxy: {
            "localhost": "http://127.0.0.1:8000"
        }
    },
    plugins: [
        react(),
        laravel({
            input: ['resources/css/app.css', 'resources/js/app.js'],
            refresh: true,
        }),
    ],
    build: {

        /** If you set esmExternals to true, this plugins assumes that 
          all external dependencies are ES modules */
     
        commonjsOptions: {
           esmExternals: true 
        },
     }
});
```
Step 6: Vite Dev Server Start
Now after installing the reactjs, we need to start the dev server for vite for that run the following command and it will watch your resources/js/app.js file and resources/css/app.css file. It also starts a vite server on http://localhost:3000. you can not open it in the browser as it is for vite hot reload and it runs in the background and watches the assets of your application like js and CSS.
```
npm run dev
```
Step 7:add vite helper to your X.blade.php file in the head section
```
@viteReactRefresh
@vite([
    'resources/css/app.scss',
    'resources/js/app.jsx'
]);
```
