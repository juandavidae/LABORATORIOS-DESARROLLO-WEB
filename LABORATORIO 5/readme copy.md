# Laboratorio: Flexbox y Diseño Responsivo con Media Queries

## 📚 Descripción

Este laboratorio tiene como objetivo que aprendas a crear diseños responsivos utilizando **Flexbox** y **Media Queries**. Se te proporcionan archivos HTML con la estructura completa de una Pokédex, y tu tarea será crear los estilos CSS necesarios para que el sitio sea totalmente responsivo.

## 🎯 Objetivos de Aprendizaje

- Comprender y aplicar las propiedades de Flexbox
- Implementar diseños responsivos usando Media Queries
- Adaptar layouts para diferentes tamaños de pantalla (mobile, tablet, desktop)
- Aplicar principios de diseño web moderno

## 📁 Estructura del Proyecto

```
flexbox/
├── index.html              # Página de Pokémons
├── trainers.html           # Página de Entrenadores
├── assets/
│   ├── css/
│   │   ├── menu.css           # Estilos del menú (A CREAR)
│   │   ├── pokemon-cards.css  # Estilos de cards de Pokémon (A CREAR)
│   │   └── trainers.css       # Estilos de cards de Entrenadores (A CREAR)
│   └── img/
└── readme.md
```

## 🚀 Instrucciones

### Paso 1: Analiza el HTML

Antes de empezar a escribir CSS, revisa cuidadosamente los archivos HTML proporcionados:
- `index.html` - Contiene el menú de navegación y 9 tarjetas de Pokémon
- `trainers.html` - Contiene el menú de navegación y 9 tarjetas de entrenadores

Identifica:
- Las clases CSS que necesitarás estilizar
- La estructura de contenedores (nav, main, section, div)
- Los elementos que deben ser flexibles

### Paso 2: Crea los Archivos CSS

Deberás crear tres archivos CSS en la carpeta `assets/css/`:

#### 1. `menu.css` - Menú de Navegación Responsivo

**Elementos a estilizar:**
- `.navbar` - Contenedor principal del menú
- `.nav-container` - Contenedor interno con Flexbox
- `.nav-logo` - Logo de la aplicación
- `.nav-menu` - Lista de navegación
- `.nav-item` - Elemento individual del menú
- `.nav-link` - Enlaces de navegación

**Requisitos con Flexbox:**
```css
/* Ejemplo de estructura básica */
.nav-container {
    display: flex;
    justify-content: space-between;  /* Distribuye logo y menú */
    align-items: center;              /* Centra verticalmente */
    flex-wrap: wrap;                  /* Permite que se envuelva en mobile */
}

.nav-menu {
    display: flex;
    gap: 2rem;                        /* Espaciado entre items */
    flex-wrap: wrap;                  /* Se envuelve si es necesario */
}
```

#### 2. `pokemon-cards.css` - Tarjetas de Pokémon

**Elementos a estilizar:**
- `.container` - Contenedor principal
- `.pokemon-grid` - Grid de tarjetas usando Flexbox
- `.pokemon-card` - Tarjeta individual
- `.pokemon-image` - Imagen del Pokémon
- `.pokemon-info` - Información del Pokémon
- `.pokemon-name` - Nombre del Pokémon
- `.pokemon-type` - Tipo del Pokémon (badge)
- Clases de tipos: `.type-electric`, `.type-grass`, `.type-fire`, `.type-water`, etc.

**Requisitos con Flexbox:**
```css
/* Ejemplo de grid con Flexbox */
.pokemon-grid {
    display: flex;
    flex-wrap: wrap;                  /* Permite múltiples filas */
    gap: 2rem;                        /* Espaciado entre tarjetas */
    justify-content: center;          /* Centra las tarjetas */
}

.pokemon-card {
    display: flex;
    flex-direction: column;           /* Apila imagen sobre info */
    flex: 1 1 calc(33.333% - 2rem);  /* 3 columnas en desktop */
    max-width: calc(33.333% - 2rem);
    min-width: 250px;                 /* Ancho mínimo */
}
```

#### 3. `trainers.css` - Tarjetas de Entrenadores

Similar a `pokemon-cards.css`, pero con:
- `.trainers-grid` - Grid de entrenadores
- `.trainer-card` - Tarjeta individual
- `.trainer-image` - Avatar del entrenador
- `.trainer-info` - Información del entrenador
- `.trainer-name`, `.trainer-region`, `.trainer-badges`, `.trainer-status`

## 📱 Media Queries - Diseño Responsivo

### ¿Qué son los Media Queries?

Los **Media Queries** permiten aplicar estilos CSS diferentes según el tamaño de la pantalla del dispositivo. Esto es fundamental para crear sitios web responsivos.

### Breakpoints Recomendados

Usa estos breakpoints estándar para tus media queries:

```css
/* Estilos base (Desktop) - Se aplican por defecto */
.pokemon-card {
    flex: 1 1 calc(33.333% - 2rem);  /* 3 columnas */
}

/* Tablet (hasta 768px) */
@media screen and (max-width: 768px) {
    .pokemon-card {
        flex: 1 1 calc(50% - 1.5rem);  /* 2 columnas */
    }
}

/* Mobile (hasta 480px) */
@media screen and (max-width: 480px) {
    .pokemon-card {
        flex: 1 1 100%;                /* 1 columna (ancho completo) */
    }
}
```

### Estructura de un Media Query

```css
/* Sintaxis básica */
@media screen and (max-width: 768px) {
    /* Estilos que se aplican cuando el ancho es <= 768px */
    .elemento {
        propiedad: valor;
    }
}
```

### Estrategia Mobile-First vs Desktop-First

En este laboratorio usamos **Desktop-First**:
1. Escribes estilos base para desktop
2. Usas `max-width` en media queries para adaptar a pantallas más pequeñas

```css
/* Base: Desktop */
.nav-menu {
    flex-direction: row;  /* Horizontal */
}

/* Mobile: Cambia a vertical */
@media screen and (max-width: 768px) {
    .nav-menu {
        flex-direction: column;  /* Vertical */
    }
}
```

## 🎨 Diseño Responsivo Requerido

### Menú de Navegación
- **Desktop**: Logo a la izquierda, menú horizontal a la derecha
- **Mobile**: Logo arriba, menú vertical debajo

### Tarjetas de Pokémon/Entrenadores
- **Desktop** (>768px): 3 tarjetas por fila
- **Tablet** (480-768px): 2 tarjetas por fila
- **Mobile** (<480px): 1 tarjeta ocupando el ancho completo

## 🎨 Personalización de Colores

**¡Usa tu creatividad!** Los colores son completamente de tu elección. Considera:

### Menú de Navegación
- Color de fondo del navbar
- Color de texto de los enlaces
- Color de hover en los enlaces

### Tarjetas
- Fondo de las tarjetas
- Colores para los badges de tipo de Pokémon
- Colores para los estados de entrenadores
- Sombras y efectos

**Recomendaciones:**
- Usa herramientas como [Coolors](https://coolors.co/) para paletas de colores
- Considera usar gradientes con `linear-gradient()`
- Mantén buen contraste para legibilidad

## 📝 Propiedades Flexbox Esenciales

### Contenedor Flex (Padre)
```css
.contenedor {
    display: flex;                    /* Activa Flexbox */
    flex-direction: row;              /* row | column | row-reverse | column-reverse */
    flex-wrap: wrap;                  /* wrap | nowrap | wrap-reverse */
    justify-content: center;          /* flex-start | flex-end | center | space-between | space-around */
    align-items: center;              /* flex-start | flex-end | center | stretch | baseline */
    gap: 1rem;                        /* Espaciado entre items */
}
```

### Items Flex (Hijos)
```css
.item {
    flex: 1 1 300px;                  /* flex-grow | flex-shrink | flex-basis */
    /* O de forma individual: */
    flex-grow: 1;                     /* Cuánto puede crecer */
    flex-shrink: 1;                   /* Cuánto puede encogerse */
    flex-basis: 300px;                /* Tamaño base */
}
```

## ✅ Checklist de Tareas

### Menu.css
- [ ] Estilos base del navbar
- [ ] Flexbox en `.nav-container` y `.nav-menu`
- [ ] Efectos hover en enlaces
- [ ] Media query para tablet (768px)
- [ ] Media query para mobile (480px)
- [ ] Menú se apila verticalmente en mobile

### Pokemon-cards.css
- [ ] Estilos del contenedor y grid
- [ ] Tarjetas con Flexbox
- [ ] Estilos de imagen y texto
- [ ] Badges de tipo con colores personalizados
- [ ] Efectos hover en tarjetas
- [ ] Media query para tablet (2 columnas)
- [ ] Media query para mobile (1 columna)

### Trainers.css
- [ ] Similar a pokemon-cards.css
- [ ] Imagen del avatar ocupa el espacio (object-fit: cover)
- [ ] Badges de estado personalizados
- [ ] Diseño responsivo 3-2-1 columnas

## 🧪 Pruebas

### Cómo Probar tu Sitio Responsivo

1. **Usando DevTools del Navegador:**
   - Presiona `F12` o `Cmd+Option+I` (Mac)
   - Activa el modo responsive: `Ctrl+Shift+M` o icono de dispositivo móvil
   - Prueba diferentes tamaños: iPhone, iPad, Desktop

2. **Breakpoints a Probar:**
   - 320px (Mobile pequeño)
   - 480px (Mobile)
   - 768px (Tablet)
   - 1024px (Desktop)
   - 1440px (Desktop grande)

3. **Verifica:**
   - ¿El menú se adapta correctamente?
   - ¿Las tarjetas muestran el número correcto de columnas?
   - ¿No hay scroll horizontal innecesario?
   - ¿Los textos son legibles en todos los tamaños?
   - ¿Las imágenes se escalan apropiadamente?

## 💡 Consejos y Mejores Prácticas

1. **Reset CSS**: Empieza con un reset básico
   ```css
   * {
       margin: 0;
       padding: 0;
       box-sizing: border-box;
   }
   ```

2. **Mobile First vs Desktop First**: Este lab usa Desktop First, pero puedes experimentar con Mobile First usando `min-width`

3. **Gap vs Margin**: Usa `gap` en contenedores flex en lugar de márgenes individuales

4. **Max-Width en Contenedores**: Limita el ancho máximo para pantallas grandes
   ```css
   .container {
       max-width: 1200px;
       margin: 0 auto;
   }
   ```

5. **Object-Fit para Imágenes**: Controla cómo se escalan las imágenes
   ```css
   .imagen {
       object-fit: cover;    /* cover | contain | fill */
       object-position: center;
   }
   ```

6. **Transiciones Suaves**: Añade transiciones para efectos hover
   ```css
   .card {
       transition: transform 0.3s ease, box-shadow 0.3s ease;
   }
   ```

## 📚 Recursos Adicionales

- [CSS Flexbox Guide - CSS Tricks](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
- [MDN - Flexbox](https://developer.mozilla.org/es/docs/Web/CSS/CSS_Flexible_Box_Layout)
- [MDN - Media Queries](https://developer.mozilla.org/es/docs/Web/CSS/Media_Queries)
- [Flexbox Froggy](https://flexboxfroggy.com/#es) - Juego para aprender Flexbox
- [Coolors.co](https://coolors.co/) - Generador de paletas de colores

## 🎓 Criterios de Evaluación

Tu laboratorio será evaluado según:

1. **Funcionalidad (40%)**
   - El diseño es responsivo en todos los tamaños
   - Las tarjetas se organizan correctamente (3-2-1 columnas)
   - El menú se adapta apropiadamente

2. **Uso de Flexbox (30%)**
   - Uso correcto de propiedades flex
   - Implementación eficiente de layouts

3. **Media Queries (20%)**
   - Breakpoints apropiados
   - Transiciones suaves entre tamaños

4. **Diseño Visual (10%)**
   - Elección de colores armoniosa
   - Espaciado y tipografía adecuados
   - Efectos y detalles visuales

## 🚀 Desafíos Extra (Opcional)

1. **Menú Hamburguesa**: Implementa un menú hamburguesa funcional en mobile
2. **Animaciones**: Añade animaciones CSS avanzadas
3. **Dark Mode**: Implementa un tema oscuro con toggle
4. **Filtros**: Añade la capacidad de filtrar Pokémon por tipo
5. **Grid Layout**: Experimenta reescribiendo algunas secciones con CSS Grid

## ❓ Preguntas Frecuentes

**P: ¿Puedo usar CSS Grid en lugar de Flexbox?**
R: El objetivo de este lab es practicar Flexbox, pero puedes experimentar con Grid como desafío extra.

**P: ¿Qué navegadores debo soportar?**
R: Chrome, Firefox, Safari y Edge en sus versiones modernas.

**P: ¿Puedo añadir JavaScript?**
R: Este laboratorio se enfoca en HTML y CSS, pero puedes añadir JS como mejora extra.

## 📧 Contacto y Soporte

Si tienes preguntas o necesitas ayuda, puedes contactar a paperez@puce.edu.ec

---

**¡Buena suerte y diviértete aprendiendo Flexbox y diseño responsivo! 🎉**
