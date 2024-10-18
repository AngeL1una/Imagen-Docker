# Crear una imagen de Docker para una aplicación Node.js

Cómo crear una imagen de Docker para una aplicación Node.js. Se parte de una imagen base de Node.js 18 en Alpine, una versión minimalista de Linux, optimizada para producción.

### pasos:

- **Dockerfile**: Se crea un archivo llamado `Dockerfile` sin extensión, donde se especifican las instrucciones para construir la imagen.
- **Imagen base**: `FROM node:18-alpine` para usar Node.js 18 en Alpine.
- **Directorio de trabajo**: `WORKDIR /app` define `/app` como el directorio de trabajo dentro de la imagen.
- **Copiar package.json**: `COPY package.json .` copia el archivo de dependencias para instalarlas luego.
- **Instalar dependencias**: `RUN npm install` para reconstruir los módulos de Node.js en un entorno Linux Alpine.
- **Copiar proyecto**: `COPY . .` copia todo el sistema de archivos del proyecto, excepto lo excluido en `.dockerignore`, al directorio de trabajo.
- **Construir para producción**: `RUN npm run build` crea la versión de producción de la aplicación.
- **Exponer puerto**: `EXPOSE 3000` hace accesible el puerto 3000 para comunicarse.

### Dockerfile

```dockerfile
FROM node:18-alpine

WORKDIR /app

COPY package.json /

RUN npm install

COPY . /

RUN npm run build

EXPOSE 3000

CMD [ "npm", "start" ]
