---

```markdown
# Infografía Interactiva: Top 5 Hallazgos - IA en Educación Inclusiva

Infografía web de tipo lista desarrollada en un único archivo HTML puro con CSS integrado. Presenta información académica de manera dinámica, moderna y responsiva, sin dependencia de librerías externas ni JavaScript.

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)
![Sin JS](https://img.shields.io/badge/0%25_JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)

---

## 📋 Contenido

La infografía sintetiza los 5 hallazgos principales extraídos del artículo de investigación sobre tecnologías de asistencia impulsadas por IA:
1. Impacto transformador de la IA en la inclusión educativa.
2. Herramientas de voz y reconocimiento del habla.
3. Procesamiento de Lenguaje Natural (NLP).
4. Limitaciones técnicas y desafíos éticos.
5. Necesidad de políticas y formación.

---

## 🏗️ Arquitectura y Construcción HTML

El archivo está construido bajo una filosofía de **minimalismo técnico** y **maximalismo visual**, cumpliendo con las siguientes directrices estructurales:

### 1. Unicidad del Archivo
Todo el proyecto (Estructura + Estilos) está contenido en un único archivo `index.html`. No existen archivos CSS externos, lo que facilita la portabilidad y el despliegue inmediato en cualquier navegador o plataforma educativa (LMS, Moodle, etc.).

### 2. Estructura Semántica Base
Se evitó el uso de `<div>` genéricos para la estructura principal, optando por etiquetas semánticas de HTML5:
*   `<header>`: Para la cabecera con el título del Top 5.
*   `<main>`: Como contenedor envolvente.
*   `<ol>` y `<li>`: Para la lista ordenada, lo cual es crucial para el acceso a lectores de pantalla y la correcta indexación del contenido secuencial.
*   `<footer>`: Para los metadatos, crédito de autoría y fuente científica.

### 3. Diseño de Dos Columnas por Ítem
Cada `<li>` fue estructurado utilizando **Flexbox** (`display: flex`) para crear un layout de dos columnas sin recurrir a floats o grids complejos:
*   **Columna Izquierda (`div.icono-contenedor`):** Aloja el emoji y la anatomía de los semicírculos animados.
*   **Columna Derecha (`div.contenido-texto`):** Aloja el título (`<h2>`) y la descripción (`<p>`). Esta columna usa `flex: 1` para ocupar el espacio restante de forma fluida.

---

## 🎨 Sistema de Diseño CSS

### Variables Custom (CSS Variables)
Se definió una paleta de colores accesible y vibrante en el `:root` para garantizar consistencia y facilitar cambios globales rápidos:
*   `--color-principal`: `#1E3A8A` (Azul profundo, da peso visual).
*   `--color-secundario`: `#10B981` (Verde tecnológico, usado para interacción).
*   `--color-acento`: `#F59E0B` (Amarillo energético, usado para destacar el subtítulo).

### Filosofía Mobile First
Los estilos base están diseñados para pantallas pequeñas (móviles), aplicando un `padding` generoso para garantizar **áreas táctiles amplias**. Las media-queries (`@media (min-width: 768px)`) se utilizan exclusivamente para escalar tipografías, íconos y espaciados en pantallas mayores.

---

## ⚙️ Ingeniería de los Efectos Interactivos

Dado que la restricción principal fue **Cero JavaScript**, la interactividad se construyó aprovechando el estado `:hover` de CSS y transformaciones geométricas.

### Efecto #1: Desplazamiento y rotación del Ícono (Semicírculos)
En lugar de usar `::before` y `::after` directamente en el contenedor del emoji (lo cual generaría conflictos de apilamiento con el texto del emoji), se crearon dos `div` físicos con clases `.antes` y `.despues`:
1.  **Anatomía:** Ambos tienen `border-radius: 50%` y `clip-path: polygon(...)` recortándolos exactamente por la mitad.
2.  **Estado Inicial:** El semicírculo azul está visible en `rotate(0deg)`. El semicírculo verde está oculto detrás con `rotate(180deg)`.
3.  **Animación (`li:hover`):** Se aplica `transform: rotate(-180deg)` al azul y `rotate(0deg)` al verde. Esto crea la ilusión óptica de que las mitades se unen mágicamente para formar un círculo completo que cambia de color.
4.  **Restricción cumplida:** `transition: all 0.4s ease-in-out` controla la suavidad del movimiento.

### Efecto #2: Línea de Menú Ondulada bajo el Título
Para lograr este efecto sin SVGs externos ni JS:
1.  **Integración:** Se insertó un `<span class="linea-ondulada">` dentro del `<h2>` con `position: absolute` en la parte inferior.
2.  **Textura:** Se utilizó un vector SVG codificado en **Base64** como propiedad `background-image`. El color de la onda está incrustado en el código Base64 (`fill='%2310B981'`).
3.  **Animación:** En estado reposo, el `width` es `0` y `opacity: 0`. Al hacer `hover` en el `<li>`, se expande al `100%` y se dispara la regla `@keyframes mover-onda`, la cual desplaza el `background-position` en el eje X de forma infinita, simulando el movimiento de una ola en el mar.

---

## 👨‍💻 Cómo Personalizar

*   **Cambiar el color de la onda:** Busca la cadena `fill='%2310B981'` en la URL del `background-image` de la clase `.linea-ondulada`. Cambia `10B981` por el código HEX de tu nuevo color (recuerda mantener el `%23` que representa el símbolo `#`).
*   **Cambiar la velocidad de la animación:** Modifica el valor de `0.4s` en las propiedades `transition` para hacer el círculo más lento o rápido. Para la onda, modifica el `1.5s` dentro de `animation: mover-onda 1.5s...`.
*   **Cambiar los íconos:** Simplemente reemplaza los textos de los emojis (🤖, 🎙️, etc.) dentro de las etiquetas `<span class="emoji">`.

---

## 📑 Créditos y Fuentes

**Autoría del Diseño Front-end:** Fuentes Rojas Luana Nathaly

**Fuente Científica (Contenido):** 
> AI-driven assistive technologies in inclusive education: benefits, challenges, and policy recommendations. 
> DOI: [https://doi.org/10.1016/j.sftr.2025.101042](https://doi.org/10.1016/j.sftr.2025.101042)

--- 
*Proyecto desarrollado con HTML5 y CSS3 puro, optimizado para acceso educativo universal.*
```
