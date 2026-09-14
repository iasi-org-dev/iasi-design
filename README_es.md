[English](README.md) | [Castellano](README.es.md)

# IASI Design

**IASI Design** define la identidad visual de IASI mediante una especificación de diseño independiente de la tecnología.

El propósito de este repositorio es describir el lenguaje visual de IASI sin hacerlo depender de una tecnología de renderizado o de un formato de salida concreto.

Por tanto, SCSS, temas de PowerPoint, hojas de estilo HTML, plantillas documentales y otros artefactos visuales no se consideran la fuente del diseño. Son **materializaciones** de una especificación común.

## Idea central

El repositorio parte de un modelo sencillo:

```text
especificación
      ↓
materialización
      ↓
artefacto
```

Por ejemplo:

```text
IASI Design
    │
    ├──► materializador SCSS ──► iasi.scss
    │
    ├──► materializador PPTX ──► iasi-theme.pptx
    │
    └──► otros materializadores ─► ...
```

Una misma identidad visual puede expresarse de forma diferente según el medio de destino, conservando su semántica.

## Especificación de diseño

La especificación fuente se expresa en **TOML**.

Describe conceptos visuales independientes de la tecnología, como:

* paleta de colores
* tipografía
* espaciado
* jerarquía visual
* roles semánticos
* superficies
* bordes
* componentes visuales reutilizables

La especificación debe describir **qué significa el diseño**, no cómo lo implementa una tecnología concreta.

Por ejemplo, un rol semántico como `primary` puede materializarse como:

* una variable CSS en SCSS,
* un color `accent` del tema de Office en PowerPoint,
* un estilo documental en otro formato.

## Variantes

IASI puede necesitar más de una variante visual.

Por ejemplo:

* default
* publication
* presentation
* website

Una variante especializa la identidad visual común de IASI sin convertirse en un sistema de diseño independiente.

Esto permite que artefactos como:

```text
iasi.scss
publication.scss
presentation.scss

iasi-theme.pptx
publication-theme.pptx
presentation-theme.pptx
```

se deriven del mismo lenguaje visual.

## Características específicas de cada destino

No todos los conceptos visuales pueden ni deben representarse en todos los formatos.

Las tecnologías web pueden disponer de elementos como:

```text
diseño responsive
media queries
estados hover y focus
posicionamiento sticky
dimensionamiento dinámico
```

PowerPoint dispone en cambio de:

```text
patrones de diapositivas
layouts
placeholders
colores de tema
fuentes de tema
geometría fija de diapositiva
```

Estas características pertenecen al materializador correspondiente, no a la especificación compartida.

El objetivo no es imponer una correspondencia uno a uno entre tecnologías diferentes.

El objetivo es conservar la **intención de diseño** a través de las distintas materializaciones.

## Estructura inicial del repositorio

El repositorio comienza deliberadamente pequeño:

```text
iasi-design/
├── README.md
└── design/
    └── iasi.toml
```

Las estructuras adicionales para variantes, destinos, esquemas, validación o materializadores se incorporarán cuando su modelo esté suficientemente entendido.

## Principios

1. **La especificación es la fuente.**
   Los SCSS, temas PPTX y demás artefactos generados son resultados derivados.

2. **Primero la semántica, después la tecnología.**
   El modelo debe expresar intención visual y no detalles de implementación.

3. **La materialización conoce su destino.**
   Tecnologías diferentes pueden representar de forma distinta un mismo concepto de diseño.

4. **Las variantes heredan la identidad.**
   Presentación, publicación y otras variantes especializan IASI Design en lugar de duplicarlo.

5. **Los artefactos generados deben ser reproducibles.**
   Una misma especificación y un mismo materializador deben producir resultados equivalentes.

6. **Empezar pequeño.**
   El modelo debe crecer a partir de necesidades reales, sin intentar describir de antemano todas las capacidades de CSS, PowerPoint o cualquier otra tecnología de renderizado.

## Estado

IASI Design se encuentra actualmente en su fase conceptual inicial.

El primer objetivo es definir una especificación `iasi.toml` pequeña pero útil y demostrar el modelo materializándola al menos en dos destinos diferentes:

```text
IASI Design → SCSS
IASI Design → PPTX
```

El modelo evolucionará a partir de esos experimentos.
