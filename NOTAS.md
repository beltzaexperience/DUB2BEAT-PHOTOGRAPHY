# DUB²BEAT PHOTOGRAPHY — Notas de cambios

## Archivos
- `index.html` — todo en uno: portada + álbum (CSS inlinado para funcionar sin servidor)
- `style.css` — CSS separado, enlazado desde index.html (versión para GitHub Pages)

## Estructura del álbum
- Dos polaroids por página sobre fondo textura diario
- Spines izquierdo y derecho en todas las páginas
- Texto dentro del polaroid: Caveat azul bic / rojo destacado
- Foto Sound: Caveat azul bic enlazado

## Páginas actuales
- sp-1: Fuego, Adicción y Muerte (izq) + Real Puerto Hispano Americano (drch)
- sp-2: Sombras de Amor (izq) + Y la Sombra Pasó a la Acción (drch, díptico)
- sp-3: Aizkolaris Doneztebe (izq) + Herminio Afonso Bilbao (drch)
- sp-4: Chica Oriental (izq, vertical) + Los Perretes Tolosa (drch) — TOTAL=4

## Navegación
- Modo DIARIO (por defecto): abre en la última página, navega hacia la primera
- Modo CRONOLÓGICO: orden tradicional, botón ⇄ en portada y álbum
- Paginación siempre cronológica: PÁG. 1 = más antigua, PÁG. 4 = más reciente
- DIAPOSITIVAS: arranca desde la última página en modo diario, pausa y reanuda desde donde está

## Para añadir páginas
1. Duplicar bloque `<div class="spread" id="sp-N">` con nuevo N
2. Actualizar `const TOTAL=N` en el JS
3. Usar la clase de ratio correcta (ver abajo)
4. La nueva página será la primera en abrirse (modo diario)

## CLASES DE RATIO (style.css)
La polaroid se dimensiona por: width = altura_disponible × (ancho_foto / alto_foto)
Usar siempre la clase correcta según dimensiones de la foto.

### Horizontales (landscape)
| Clase               | Ratio  | Uso                      |
|---------------------|--------|--------------------------|
| mount-r-l-3-2       | 1.500  | 3:2 landscape            |
| mount-r-l-4-3       | 1.333  | 4:3 landscape            |
| mount-r-l-16-9      | 1.778  | 16:9 landscape           |
| mount-r-l-1600x957  | 1.672  | Aizkolaris, Los Perretes |

### Cuadradas
| Clase               | Ratio  | Uso                  |
|---------------------|--------|----------------------|
| mount-r-square      | 1.000  | 1:1 cuadrada         |
| (defecto)           | 0.813  | ~cuadrada Flickr _b  |

### Verticales (portrait)
| Clase                | Ratio  | Uso                        |
|----------------------|--------|----------------------------|
| mount-r-p-3-4        | 0.750  | 3:4 portrait               |
| mount-r-p-2-3        | 0.667  | 2:3 portrait (1067×1600)   |
| mount-r-p-1067x1800  | 0.593  | Chica Oriental             |

## ⚠️ NORMA SAGRADA — IMÁGENES
- SIEMPRE: `width:100%; height:auto` en todas las imágenes
- NUNCA: `max-height` en imágenes — achata y rompe proporciones
- NUNCA: `height` fijo en imágenes
- El ratio del polaroid (clase `mount-r-*`) controla el tamaño
- La foto respeta sus proporciones sola

- La polaroid SIEMPRE abraza la foto — nunca al revés
- NUNCA cortar la foto
- Foto a full sin blanco inferior: añadir clase `mount-static` → `height:auto; overflow:visible`
- Foto grande landscape (sp-3 Aizkolaris, sp-4 Perretes): `mount-static` + `width:min(62%, calc((100vh - 10rem) * ratio))`
- Foto vertical con texto (sp-4 Chica Oriental): `mount-r-p-1067x1800`
- Siempre dar dimensiones de la foto al añadir nueva página

## PORTADA — Logo D²B
- **Desktop**: `position:absolute; top/right: clamp(.8rem,3%,1.8rem)` dentro de `.cover-content`
  — flota en el área superior derecha de la columna de texto, sin ocupar espacio en el flujo
- **Móvil**: `position:static` — fluye en la columna después de la firma "Luis Beltza"
- El logo está en el HTML **fuera de `#titleRow`**, como hermano después de `.cover-sig`
- `#titleRow` solo contiene `#titleCol` (título DUB²/BEAT + regla)

## MÓVIL
Breakpoint: `@media (max-width:700px),(orientation:portrait)`

### Portada móvil (orden visual de arriba a abajo)
1. `.p-top` — links wrapeados
2. Spine — barra horizontal 18px
3. Título DUB² / BEAT (fitLines sobre ancho de columna)
4. Citas (svg fit-width)
5. Firma Luis Beltza
6. Logo D²B (52% ancho, centrado)
7. Citas Capa / Cartier-Bresson
8. Polaroid Marvin (autorretrato, ancho 100%)
9. Spine — barra horizontal 18px
10. `.p-nav` — botones

### Álbum móvil
- Spines laterales → 6px (decorativos)
- Polaroids apiladas en columna, 92% ancho, sin rotación, `height:auto`
- `spread-diario` scrollable verticalmente dentro del área fija
- `alb-top` y `alb-nav` wrapeados con fuente reducida
