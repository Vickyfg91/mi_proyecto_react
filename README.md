# Proyecto: Despliegue automático en Render

Este proyecto guía es una guia para clonar y crear un repositorio en GitHub y desplegarlo en la plataforma Render. El objetivo es proporcionar una guía paso a paso para desplegar una aplicación React en un entorno de producción.

## Requisitos

Antes de comenzar, asegúrate de tener:

1. **Node.js y npm**
2. **Cuenta en GitHub**
3. **Cuenta en Render**

A continuación, se detalla los pasos a seguir y cómo desplegar el sistema completo.

---


## **Pasos a seguir**

### **1. Clonación del Repositorio**

Clona el repositorio original en tu máquina local

1. Clona el repositorio nombralo y posicionate en el directorio:
   ```bash
   git clone https://github.com/rpiealb297/despliegue-apache
   cd despliegue-apache
   ```

2. Crea el Dockerfile:
   ```bash
   nano Dockerfile
   ```
  ```bash
    # Usa una imagen base de Node.js
    FROM node:18

    # Establece el directorio de trabajo
    WORKDIR /app

    # Copy package.json y package-lock.json
    COPY package*.json ./

    # Install dependencies
    RUN npm install

    # Copy ther rest of your app
    COPY . .

    # Compiling
    RUN npm run build
    
    # Expose the port your app runs on
    EXPOSE 3000

    # Define the command to run your app
    CMD ["npm", "start"]
    ```
### **2. Creación del Repositorio en GitHub**
- Crea un nuevo repositorio en tu cuenta de GitHub con el nombre mi_proyecto_react.

### **3. Subida del Proyecto a GitHub**
- Conecta tu nuevo proyecto modificado con el Dockerfile y sube los cambios
  ```bash
    git branch -m master main
    git remote remove origin
    git remote add origin <URL_DE_TU_NUEVO_REPOSITORIO>
    git add .
    git commit -m "Subida inicial del proyecto React"
    git push -u origin main
  ```
### **4. Comprobación de la Aplicación en Local**
- Antes de desplegar en el entorno de producción, asegúrate de que la aplicación funciona correctamente en tu entorno local:
  ```bash
    npm install
    npm start
  ```
- La aplicación debería estar disponible en http://localhost:3000.

---

## **Despliegue en Render**
- Accede al la pagina de [render](https://render.com/)
1. Inicia sesión en Render.
2. Selecciona "Web Service".
3. Conecta tu cuenta de GitHub.
4. Selecciona el repositorio que acabas de crear.
5. Elige el tipo de instancia, si no quieres pagar el Free.
6. Clica en "Deploy Web Service".Se iniciara el proceso de despliegue en el servidor.
7.  Una vez finalizado, Render te generara una URL donde esta albergada el despligue de la web.