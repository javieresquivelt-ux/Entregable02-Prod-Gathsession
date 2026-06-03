# GathSession - Build Your Best Community

Proyecto formativo centrado en la construcción de una interfaz de usuario (Landing Page) moderna. Este proyecto dutiliza metodologías CSS para lograr layouts flexibles y mantenibles, aplicando principios rigurosos de diseño responsivo (Mobile-First).

## 🎯 Objetivos
*   **Dominio Arquitectónico:** Implementar la arquitectura Sass 7-1 junto con la metodología BEM (Block Element Modifier) para escribir un código limpio, escalable y sin especificidad innecesaria.
*   **Modernización de Herramientas:** Adoptar el uso de Vite como empaquetador ultrarrápido y utilizar módulos nativos de Dart Sass (`@use`) para gestionar variables y funciones de color.
*   **Precisión de Layouts:** Utilizar Flexbox avanzado (desacoplamiento de ejes con `align-self`) y CSS Grid asimétrico para crear diseños que fluyan armónicamente entre dispositivos.
*   **Estética:** Aplicar principios de diseño moderno, tales como jerarquía tipográfica marcada, efectos "Glass" sutiles (Translucidez en iconos), micro-animaciones (hover), animaciones de flotación y espaciados de respiración (`whitespace`).

---

## 🗂️ Estructura de Archivos

```text
/ (Raíz del proyecto)
├── index.html            # Estructura semántica de la aplicación
├── package.json          # Dependencias y scripts automatizados (dev, build)
├── README.md             # Esta documentación
├── memory.md             # Registro de cambios del proyecto
├── task.md               # Planes de trabajo
├── vite.config.js        # Configuración del servidor/empaquetador Vite
├── public/               # Archivos estáticos inyectables (Favicons, webmanifest, SVGs decorativos)
├── agent/                # Documentación interna de Skills y Lecciones Técnicas
├── template/             # Mockups de diseño visual de referencia
└── src/
    ├── main.js           # Punto de entrada de JavaScript
    ├── assets/
    │   ├── img/          # Imágenes de contenido (image1-5.png, logo, ellipses)
    │   └── icon/         # Iconografía en formato SVG
    └── scss/             # Estilos preprocesados (Sass 7-1)
        ├── app.scss      # Archivo central de compilación (Manager)
        ├── _settings.scss
        ├── abstracts/    # Herramientas sin salida directa a CSS
        │   ├── _index.scss
        │   ├── _variables.scss # Tokens de diseño (Colores, tipografía)
        │   └── _mixins.scss    # Breakpoints y utilidades
        ├── base/         # Reglas globales y reseteos
        │   ├── _index.scss
        │   ├── _reset.scss
        │   └── _typography.scss
        ├── components/   # Componentes reutilizables
        │   ├── _index.scss
        │   └── _buttons.scss # Botones y CTAs
        └── layout/       # Bloques estructurales principales de la página
            ├── _index.scss
            ├── _container.scss   # Rejilla y márgenes del sitio
            ├── _header.scss      # Navegación y branding superior
            ├── _hero.scss        # Sección de impacto con grid asimétrico de 5 fotos
            └── _categories.scss  # Bloques "badge" informativos (Features)
```

---

## 🧩 Secciones del Sitio (Características CSS)

### 1. Header (`_header.scss`)
*   **Layout:** Navegación superior implementada con `display: flex; justify-content: space-between;` para apartar naturalmente el logotipo de los enlaces.
*   **Interacción:** Enlaces semánticos con micro-transiciones de color al hacer `:hover`, garantizando legibilidad. Menú hamburguesa en móvil con animación a cruz (X) mediante clases BEM.

### 2. Hero (`_hero.scss`)
*   **Asimetría Controlada:** Layout vertical apilado en móvil y distribuido al `50%` en escritorio usando Flexbox (`flex-direction: row`).
*   **Desacoplamiento Vertical:** Empleo de `align-self: flex-start` en el contenedor de texto y `align-self: center` en el grid de imágenes, evitando el *stretch* o el espacio muerto.
*   **Grid Asimétrico de 5 Fotos:** CSS Grid de 3 columnas × 3 filas con posicionamiento `grid-row` / `grid-column` para crear una disposición irregular:
    *   `image4.png`: columna 1, filas 1-2 (2 filas)
    *   `image3.png`: columna 1, fila 3
    *   `image1.png`: columna 2, fila 1
    *   `image2.png`: columna 2, filas 2-3 (2 filas)
    *   `image5.png`: columna 3, filas 1-3 (3 filas) con `object-fit: contain`
*   **Animación de Flotación (`floatGrid`):** El grid completo levita suavemente con `translateY(-12px)` en un loop infinito de 6 segundos, aportando dinamismo.
*   **Decoraciones SVG:** Dos elipses decorativas (`ellipse1.svg`, `ellipse2.svg`) posicionadas absolutamente en la esquina inferior derecha, visibles solo en desktop (≥1200px).

### 3. Categorías / Features (`_categories.scss`)
*   **Badge Design:** En lugar de ser tarjetas grandes (banners), son pequeños componentes horizontales ubicados estratégicamente bajo el Hero.
*   **Estrategia Flex-Wrap Dinámica:** 
    *   **Móvil:** Usa `flex-wrap: wrap` con `justify-content: center` para empujar la tercera tarjeta a una línea inferior centrada.
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
*   **Principal:** `Poppins, sans-serif` (Pesos: 300, 400, 500). Usada para UI general, botones, cuerpo de texto y descripciones de categorías.
*   **Secundaria (Impacto):** `Merriweather, serif` (Pesos variables, enfocado en 700+). Usada exclusivamente en el título gigante (Hero `<h1>`) para inyectar una sensación editorial y premium.

---

## 🛠️ Tecnologías Utilizadas
*   **HTML5 Semántico:** Uso correcto de etiquetas (main, header, section, figure).
*   **Sass / SCSS (Dart Sass):** Aprovechamiento de módulos nativos (`@use 'sass:color'`) y arquitectura limpia 7-1.
*   **CSS Grid & Flexbox:** Grid asimétrico para el collage de imágenes, Flexbox para layouts de navegación y componentes en línea.
*   **Vite:** Servidor de desarrollo HMR ultrarrápido y orquestador de empaquetado para producción.
*   **NPM / Node.js:** Gestión de dependencias y scripts de automatización.

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
4. Para construir la versión final de producción:
   ```bash
   npm run build
   ```

---

## 🧠 Aprendizajes Clave (Reflexión Técnica)
1. **El contexto Macro:** Identificar componentes por secciones aisladas puede llevar a errores de escala (ej. tratar las *categorías* como banners enteros cuando eran simples *badges* en línea).
2. **"Stretch" Invisible:** Comprender cómo se comporta Flexbox por defecto (`align-items: stretch`) en contenedores columna previene que los elementos internos colapsen y destruyan los posicionamientos absolutos. El uso de `align-self` lo soluciona drásticamente.
3. **Márgenes Negativos Controlados:** Aplicar un `margin-top` negativo (ej. `-40px`) en una sección subsecuente es una técnica segura para succionar la sección hacia arriba sin alterar las medidas fijas del ancestro principal.
4. **Grid Asimétrico con CSS Grid:** El uso de `grid-row` y `grid-column` permite crear collages irregulares sin depender de posicionamiento absoluto, manteniendo el flujo del documento.
5. **Stacking Context y Overflow:** Los pseudo-elementos y elementos absolutamente posicionados pueden ser recortados por `overflow: hidden` de ancestros intermedios. La solución es colocarlos como hijos directos del contenedor raíz con `position: relative`.
6. **Animación de Flotación en Grids:** Aplicar `translateY` en un keyframe sobre un grid completo, con `position: relative` para evitar romper el flujo, genera un efecto visual premium sin afectar el layout subyacente.
