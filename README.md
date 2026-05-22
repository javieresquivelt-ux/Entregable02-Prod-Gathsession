# GathSession - Build Your Best Community

Proyecto formativo centrado en la construcción de una interfaz de usuario (Landing Page) moderna. Este proyecto demuestra el uso de metodologías CSS para lograr layouts flexibles y mantenibles, aplicando principios rigurosos de diseño responsivo (Mobile-First).

## 🎯 Objetivos
*   **Dominio Arquitectónico:** Implementar la arquitectura Sass 7-1 junto con la metodología BEM (Block Element Modifier) para escribir un código limpio, escalable y sin especificidad innecesaria.
*   **Modernización de Herramientas:** Adoptar el uso de Vite como empaquetador ultrarrápido y utilizar módulos nativos de Dart Sass (`@use`) para gestionar variables y funciones de color.
*   **Precisión de Layouts:** Utilizar Flexbox de forma avanzada (desacoplamiento de ejes con `align-self`, estrategias de `flex-wrap` dinámico) para crear diseños que fluyan armónicamente entre dispositivos.
*   **Estética:** Aplicar principios de diseño moderno, tales como jerarquía tipográfica marcada, efectos "Glass" sutiles (Translucidez en iconos), micro-animaciones (hover) y espaciados de respiración (`whitespace`).

---

## 🗂️ Estructura de Archivos

```text
/ (Raíz del proyecto)
├── index.html            # Estructura semántica de la aplicación
├── package.json          # Dependencias y scripts automatizados (dev, build)
├── README.md             # Esta documentación
├── vite.config.js        # Configuración del servidor/empaquetador Vite
├── public/               # Archivos estáticos inyectables (Favicons, webmanifest)
├── agent/                # Documentación interna de Skills y Lecciones Técnicas
└── src/
    ├── main.js           # Punto de entrada de JavaScript
    ├── assets/
    │   ├── img/          # Imágenes de contenido (ej. content.png)
    │   └── icon/         # Iconografía en formato SVG
    └── scss/             # Estilos preprocesados (Sass 7-1)
        ├── app.scss      # Archivo central de compilación (Manager)
        ├── abstracts/    # Herramientas sin salida directa a CSS
        │   ├── _index.scss
        │   ├── _variables.scss # Tokens de diseño (Colores, tipografía)
        │   └── _mixins.scss    # Breakpoints y utilidades
        ├── base/         # Reglas globales y reseteos
        │   ├── _index.scss
        │   ├── _reset.scss
        │   └── _typography.scss
        └── layout/       # Bloques estructurales principales de la página
            ├── _index.scss
            ├── _header.scss     # Navegación y branding superior
            ├── _hero.scss       # Sección de impacto principal asimétrica
            └── _categories.scss # Bloques "badge" informativos (Features)
```

---

## 🧩 Secciones del Sitio (Características CSS)

### 1. Header (`_header.scss`)
*   **Layout:** Navegación superior implementada con `display: flex; justify-content: space-between;` para apartar naturalmente el logotipo de los enlaces.
*   **Interacción:** Enlaces semánticos con micro-transiciones de color al hacer `:hover`, garantizando legibilidad. Ocultamiento de la navegación en vistas móviles a la espera de un menú hamburguesa.

### 2. Hero (`_hero.scss`)
*   **Asimetría Controlada:** Layout vertical apilado en móvil y distribuido al `50%` en escritorio usando Flexbox (`flex-direction: row`).
*   **Desacoplamiento Vertical:** Empleo inteligente de `align-self: flex-start` en el contenedor de texto y `align-self: center` en la imagen, evitando el *stretch* o el espacio muerto (gap invisible) que genera `align-items: center` a nivel general.
*   **Fluid Image & Float:** La imagen fotográfica principal usa `width: 100%; max-width: 450px;` para ser fluida, complementada con una animación de *keyframes* (`floatImage`) para flotar delicadamente.

### 3. Categorías / Features (`_categories.scss`)
*   **Badge Design:** En lugar de ser tarjetas grandes (banners), son pequeños componentes horizontales ubicados estratégicamente bajo el Hero.
*   **Estrategia Flex-Wrap Dinámica:** 
    *   **Móvil (iPhone XR):** Usa `flex-wrap: wrap` con `justify-content: center` para empujar la tercera tarjeta a una línea inferior centrada, salvando desbordamientos en pantallas muy angostas.
    *   **Desktop:** Forzado a `flex-wrap: nowrap` para alinear limpiamente las tres cajas en una sola línea horizontal.
*   **Look & Feel:** Uso de iconos anidados en un `.icon-wrapper` transparente `background-color: rgba(#FFFFFF, 0.08);` con `flex-shrink: 0;` para que no se deformen, emulando un efecto *Glass* sobrio.

---

## 🎨 Design System

### Paleta de Colores
*   **Negro Principal (`#2B2D38`):** Color de fondo general de la aplicación. Otorga un ambiente nocturno, profesional y elegante que resalta las imágenes.
*   **Blanco (`#FFFFFF`):** Usado en textos principales e iconos, así como en opacidades fraccionales (`rgba`) para los efectos translúcidos (tarjetas y cajas de iconos).
*   **Rosa Acento (`#DB2A6B`):** El color de impacto ("Call to Action"). Usado en el botón principal ("Get Started") y detalles de branding para guiar el ojo del usuario.
*   **Gris (`#ABABAB`):** Aplicado a subtítulos y texto secundario para reducir fatiga visual y jerarquizar la información.

### Tipografías
*   **Principal:** `Poppins, sans-serif` (Pesos: 300, 400, 500, 600). Usada para UI general, botones, cuerpo de texto y descripciones de categorías. Tamaño base escalado fluidamente (`0.875rem` - `1rem`).
*   **Secundaria (Impacto):** `Merriweather, serif` (Pesos variables, enfocado en 700+). Usada exclusivamente en el título gigante (Hero `<h1>`) para inyectar una sensación editorial y premium, con un escalado que llega a `2.5rem`+ en escritorio.

---

## 🛠️ Tecnologías Utilizadas
*   **HTML5 Semántico:** Uso correcto de etiquetas (main, header, section, figure).
*   **Sass / SCSS (Dart Sass):** Aprovechamiento de módulos nativos (`@use 'sass:color'`) y arquitectura limpia 7-1.
*   **Vite:** Servidor de desarrollo HMR ultrarrápido y orquestador de empaquetado para producción.
*   **NPM / Node.js:** Gestión de dependencias y scripts de automatización (ej. generación de Favicons/PWA icons usando `sharp-cli`).

---

## 🚀 Instalación y Uso

1. Clonar el repositorio localmente.
2. Instalar las dependencias de Node:
   ```bash
   npm install
   ```
3. Levantar el servidor de desarrollo en vivo:
   ```bash
   npm run dev
   ```
4. Para construir la versión final de producción y sincronizar esta documentación en la carpeta `dist/`:
   ```bash
   npm run build
   ```

---

## 🧠 Aprendizajes Clave (Reflexión Técnica)
1. **El contexto Macro:** Identificar componentes por secciones aisladas puede llevar a errores de escala (ej. tratar las *categorías* como banners enteros cuando eran simples *badges* en línea).
2. **"Stretch" Invisible:** Comprender cómo se comporta Flexbox por defecto (`align-items: stretch`) en contenedores columna previene que los elementos internos colapsen y destruyan los posicionamientos absolutos (flechas o pseudo-elementos vinculados). El uso de `align-self` lo soluciona drásticamente.
3. **Márgenes Negativos Controlados:** Las grillas flex no siempre ofrecen la proximidad deseada debido a los elementos adyacentes. Aplicar un `margin-top` negativo (ej. `-40px`) en una sección subsecuente es una técnica avanzada y segura para succionar la sección hacia arriba sin alterar las medidas fijas del ancestro principal.
