# SOCIAL OPLESK
### 🏴‍☠️ HACKS 
<br/>

## ⚡️ Realizar los 3 Hacks ➔ (Ejercicios) ⚡️

📚 docs [comandos git 1](https://gist.github.com/dasdo/9ff71c5c0efa037441b6) | [comandos git 2](https://github.com/joshnh/Git-Commands/blob/master/READMEes.md) | [comandos git 3](https://confluence.atlassian.com/bitbucketserver/basic-git-commands-776639767.html) | [config cuenta](https://git-scm.com/book/es/v2/Inicio---Sobre-el-Control-de-Versiones-Configurando-Git-por-primera-vez) 
---


```diff
- NOTA HACER LAS PRÁCTICAS MEDIANTE LA CONSOLA DE GIT BASH  
```
|Hacks | Details | 
|----------|---------|
| H-1      | Enviar un saludo de hola mundo |
| H-2      | Detectar rama |
| H-3      | Detectar pull request |
| H-4      | Crear un proceso de minify para un archivo .js | 
| H-5      | Enviar mensaje a telegram | 

<br/> 


## 🏆 H-1
Enviar un mensaje de hola mundo cuando se haga un push a la rama main

1. crear el directorio .github/workflows

2. Crear el archivo hola.yml

3. Ejemplo:
```
name: Hola Mundo

on:
  push:
    branches:
      - main

jobs:
  saludo:
    runs-on: ubuntu-latest
    
    steps:
    - name: Download Source
      uses: actions/checkout@v4
      
    - name: Say Hola Mundo
      run: echo "¡Hola mundo! Se ha realizado un push a la rama main."
```
<br/>


## 🏆 H-2
Enviar un mensaje de (Hola Developer sino Hola Main) cuando se haga un push a las ramas
correspondientes de: Main y Developer.

1. crear el directorio .github/workflows

2. Crear el archivo detectar_rama.yml

3. Ejemplo:
   
```
 name: SayHello

 on:
   push:
     branches:
       - develop
       - main

   pull_request:
     branches:
       - main
       - develop

       
 jobs:
  detect-branch:
     runs-on: ubuntu-latest

     steps:
       - name: Download Source
         uses: actions/checkout@v4
          
       - name: Say Hello Main
         if: ${{ github.ref == 'refs/heads/main' }}
         run: echo "Hello, main!"
```
<br/>


## 🏆 H-3
Enviar un mensaje cuando se detecte un pull_request a la rama main

1. crear el directorio .github/workflows

2. Crear el archivo detectar_pr.yml

3. Ejemplo:

```
        - name: PR
          if: github.event_name == 'pull_request'
          run: echo "hello pull request"  
```


<br/>


## 🏆 H-4
Enviar un mensaje cuando se detecte un pull_request a la rama main

💡 [link: auto-commit-action:](https://github.com/stefanzweifel/git-auto-commit-action)

1. crear el directorio .github/workflows

2. Crear el archivo minify.yml

3. Otorgar permiso de escritura en github, para que el auto-commit se pueda ejecutar

4. Ejemplo:

```
  steps:
      - uses: actions/checkout@v4

      - name: Setup Node.js
        uses: actions/setup-node@v2
        with:
          node-version: '20'  

      - name: Install minify
        run: npm install minify -g

      - name: Minify JavaScript
        run: minify main.js > main.min.js

      - name: Commit minified file
        uses: stefanzweifel/git-auto-commit-action@v5
        
        with:
          commit_message: "Minify JavaScript"
```
<br/>


## 🏆 H-5
Enviar un mensaje cuando se detecte un pull_request a la rama main

💡 [link: telegram-action:](https://github.com/appleboy/telegram-action)

1. crear el directorio .github/workflows

2. Crear el archivo telegram.yml

3. Crear canal en telegram

4. Registrar el "token y id" de telegram en el baùl de secretos de github
   
. Ejemplo:

```
name: telegram message
on: [push]
jobs:

  build:
    name: Build
    runs-on: ubuntu-latest
    steps:
      - name: send telegram message on push
        uses: appleboy/telegram-action@master
        with:
          to: ${{ secrets.TELEGRAM_CHAT_ID }}
          token: ${{ secrets.TELEGRAM_BOT_TOKEN }}
          message: |
            ${{ github.actor }} created commit:
            Commit message: ${{ github.event.commits[0].message }}
            Repository: ${{ github.repository }}
```
---
<h3 align="center">SOCIAL OPLESK</h3>

