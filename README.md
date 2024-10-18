# 🌐 Proyecto Node.js con Docker  Angel Luna Lugo

![Node.js](https://img.shields.io/badge/Node.js-18.x-brightgreen?style=flat-square)
![Docker](https://img.shields.io/badge/Docker-19.x-blue?style=flat-square)
![Alpine](https://img.shields.io/badge/Alpine-Linux-orange?style=flat-square)

## 📦 Descripción del Proyecto

Este proyecto es una aplicación Node.js empaquetada en una imagen de Docker basada en Node.js 18 en Alpine. Alpine es una versión minimalista de Linux, optimizada para entornos de producción, lo que hace que la imagen sea más ligera y rápida.

## 🛠️ Tecnologías Utilizadas

- **Node.js 18**: Plataforma de desarrollo basada en JavaScript.
- **Docker**: Plataforma para desarrollar, desplegar y ejecutar aplicaciones dentro de contenedores.
- **Alpine Linux**: Distribución de Linux ligera, rápida y segura para entornos de producción.

## 🚀 Instrucciones para Construir la Imagen

Sigue estos pasos para crear y ejecutar la imagen de Docker de la aplicación:

1. **Clonar el Repositorio**:
    ```bash
    git clone https://github.com/usuario/nombre-del-repositorio.git
    cd nombre-del-repositorio
    ```

2. **Construir la Imagen Docker**:
    ```bash
    docker build -t nombre-de-imagen .
    ```

3. **Ejecutar el Contenedor**:
    ```bash
    docker run -p 3000:3000 nombre-de-imagen
    ```

4. **Acceder a la Aplicación**:
    - La aplicación estará disponible en: [http://localhost:3000](http://localhost:3000)
  
3. **Ejecutar el .dockerignorer**:
    ```A continuación se muestra un ejemplo del archivo .dockerignore utilizado para optimizar la construcción de la imagen:
      Dockerfile
    .dockerignore
    node_modules
    npm-debug.log
    README.md
    .next
    .git

    ```


## 📄 Dockerfile

```dockerfile
FROM node:18-alpine

WORKDIR /app

COPY package.json /

RUN npm install

COPY . /

RUN npm run build

EXPOSE 3000

CMD [ "npm", "start" ]

