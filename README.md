# 📦 Box Shadow Generator 🎨

¡Bienvenido al **Box Shadow Generator**! Este proyecto es una herramienta interactiva diseñada para ayudarte a generar y personalizar sombras (`box-shadow`) en CSS de manera visual y dinámica. Fue desarrollado con el objetivo de practicar y reforzar conceptos clave de **JavaScript**, como la manipulación del DOM, eventos y la generación de código CSS en tiempo real.

## 🚀 Características principales

- **Interfaz intuitiva**: Deslizadores y selectores de color para ajustar los parámetros de la sombra.
- **Visualización en tiempo real**: Observa cómo cambia la sombra en un elemento cuadrado mientras ajustas los valores.
- **Generación de código CSS**: Obtén el código CSS correspondiente a la sombra generada.
- **Copiar al portapapeles**: ¡Copia el código generado con un solo clic!
- **Sombra interior (inset)**: Opción para aplicar la sombra dentro del elemento.

## 🛠️ Tecnologías utilizadas

- **HTML**: Estructura básica del formulario y elementos interactivos.
- **CSS**: Estilos para la interfaz de usuario y la visualización de la sombra.
- **JavaScript**: Lógica para manejar eventos, calcular valores y generar el código CSS.

## 🎨 Cómo funciona

1. **Ajusta los deslizadores**: Cambia los valores de:
   - **Horizontal Shadow** (Sombra horizontal)
   - **Vertical Shadow** (Sombra vertical)
   - **Blur Radius** (Radio de desenfoque)
   - **Spread Radius** (Radio de expansión)
   - **Shadow Color** (Color de la sombra)
   - **Shadow Color Opacity** (Opacidad del color)
   - **Inset Shadow** (Sombra interior)

2. **Visualiza los cambios**: El cuadrado en la parte superior reflejará los ajustes en tiempo real.

3. **Copia el código**: El código CSS generado se muestra en un cuadro de texto. Haz clic en el botón **"Copy"** para copiarlo al portapapeles.

## 📂 Estructura del proyecto

El proyecto consta de tres archivos principales:

1. **`index.html`**: Contiene la estructura HTML del formulario y los elementos interactivos.
2. **`styles.css`**: Define los estilos visuales de la interfaz y la animación.
3. **`script.js`**: Implementa la lógica para manejar eventos, calcular valores y generar el código CSS.

## 🖥️ Captura de pantalla

![Captura de pantalla del Box Shadow Generator](screenshot.png)  
*(Nota: Agrega una captura de pantalla de tu proyecto aquí)*

## 📝 Código de ejemplo

### HTML
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Box Shadow Generator</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="container">
        <div class="result">
            <div id="element"></div>
        </div>
        <div class="sliders">
            <!-- Deslizadores y selectores de color -->
        </div>
    </div>
    <script src="script.js"></script>
</body>
</html>
```
### CSS

```css
body {
    background-color: #2288ff;
    color: #ffffff;
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
    max-height: 100vh;
}

.container {
    background-color: #34495e;
    border-radius: 10px;
    box-shadow: 0 20px 40px rgba(0, 0, 0, 0.2);
    max-width: 600px;
    margin: 75px auto;
    padding: 40px;
}

#element {
    height: 120px;
    width: 120px;
    background-color: #ffffff;
    box-shadow: 0 0 20px rgba(0, 0, 0, 0.5);
}
/* Estilos para los deslizadores */
/* .....
```

### JavaScript

```javascript
const elem = document.getElementById('element');
const code = document.getElementById('code');
const sliders = document.querySelectorAll('.sliders input');

sliders.forEach((slider) => slider.addEventListener('input', generateShadow));

function generateShadow() {
    const shadowParams = generateShadowParams();
    const boxShadow = createBoxShadow(...shadowParams);
    applyShadow(elem, boxShadow);
    updateCode(boxShadow);
}

function generateShadowParams() {
    const hShadow = parseInt(document.getElementById('h-shadow').value);
    const vShadow = parseInt(document.getElementById('v-shadow').value);
    const blurRadius = parseInt(document.getElementById('blur-radius').value);
    const spreadRadius = parseInt(document.getElementById('spread-radius').value);
    const shadowColor = document.getElementById('shadow-color').value;
    const shadowColorOpacity = parseFloat(document.getElementById('shadow-color-opacity').value).toFixed(1);
    const shadowInset = document.getElementById("shadow-inset").checked;

    return [hShadow, vShadow, blurRadius, spreadRadius, shadowColor, shadowColorOpacity, shadowInset];
}

function createBoxShadow(hShadow, vShadow, blurRadius, spreadRadius, color, opacity, inset) {
    const shadow = inset ? 'inset' : '';
    const rgbaColor = hexToRGBA(color, opacity);
    return `${shadow} ${hShadow}px ${vShadow}px ${blurRadius}px ${spreadRadius}px ${rgbaColor}`;
}

function hexToRGBA(hex, opacity) {
    const r = parseInt(hex.substr(1, 2), 16);
    const g = parseInt(hex.substr(3, 2), 16);
    const b = parseInt(hex.substr(5, 2), 16);
    return `rgba(${r}, ${g}, ${b}, ${opacity})`;
}

function applyShadow(element, boxShadow) {
    element.style.boxShadow = boxShadow;
}

function updateCode(text) {
    code.textContent = `box-shadow: ${text};`;
}

function copyCode() {
    const codeText = code.textContent;
    navigator.clipboard.writeText(codeText)
        .then(() => alert('Code copied to clipboard!'));
}

window.onload = generateShadow;
```

## 🎯 Objetivos del proyecto
Este proyecto fue creado para:

- Practicar la manipulación del DOM con JavaScript.

- Entender cómo funcionan las sombras en CSS (box-shadow).

- Implementar eventos en tiempo real para actualizar la interfaz de usuario.

- Generar código CSS dinámicamente y permitir su copia al portapapeles.

## 🛠️ Cómo utilizar este proyecto desde GitHub

Si deseas clonar, ejecutar o contribuir a este proyecto, sigue estos pasos:

### 1. Clonar el repositorio

Primero, abre tu terminal y ejecuta el siguiente comando para clonar el repositorio en tu máquina local:

```bash
git clone https://github.com/tu-usuario/box-shadow-generator.git
```

Reemplaza tu-usuario con tu nombre de usuario de GitHub o el nombre del propietario del repositorio.

### 2. Navegar al directorio del proyecto
Una vez clonado, navega al directorio del proyecto:

```bash
cd box-shadow-generator
```

### 3. Abrir el proyecto
Puedes abrir el proyecto en tu editor de código favorito (por ejemplo, Visual Studio Code):

```bash
code .
```

### 4. Ejecutar el proyecto
Este proyecto es una aplicación web estática, por lo que no requiere un servidor backend. Simplemente abre el archivo index.html en tu navegador:

- Haz doble clic en el archivo index.html desde tu explorador de archivos.

- O, si estás usando Visual Studio Code, puedes instalar la extensión Live Server y hacer clic en Go Live en la barra inferior para abrir el proyecto en tu navegador.