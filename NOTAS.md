# DUB²BEAT PHOTOGRAPHY — Notas de cambios

## Archivos
- `index.html` — todo en uno: portada + álbum
- `style.css` — CSS separado, enlazado desde index.html

## Estructura del álbum
- Dos polaroids por página sobre fondo textura diario
- Spines izquierdo y derecho en todas las páginas
- Texto dentro del polaroid: Caveat azul bic / rojo destacado
- Foto Sound: Caveat azul bic enlazado

## Páginas actuales
- sp-1: Fuego, Adicción y Muerte + Real Puerto Hispano Americano
- sp-2: Sombras de Amor + Y la Sombra Pasó a la Acción (díptico)
- sp-3: Tolosa (Abril 2026) — Los Perretes (a full, sin inclinación)
- sp-4: Chica Oriental (vertical, izquierda) — TOTAL=4

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
| Clase               | Ratio  | Uso                  |
|---------------------|--------|----------------------|
| mount-r-l-3-2       | 1.500  | 3:2 landscape        |
| mount-r-l-4-3       | 1.333  | 4:3 landscape        |
| mount-r-l-16-9      | 1.778  | 16:9 landscape       |
| mount-r-l-1600x957  | 1.672  | Tolosa 1600x957      |

### Cuadradas
| Clase               | Ratio  | Uso                  |
|---------------------|--------|----------------------|
| mount-r-square      | 1.000  | 1:1 cuadrada         |
| (defecto)           | 0.813  | ~cuadrada Flickr _b  |

### Verticales (portrait)
| Clase                | Ratio  | Uso                  |
|----------------------|--------|----------------------|
| mount-r-p-3-4        | 0.750  | 3:4 portrait         |
| mount-r-p-2-3        | 0.667  | 2:3 portrait         |
| mount-r-p-1067x1800  | 0.593  | Chica Oriental       |

## ⚠️ NORMA SAGRADA — IMÁGENES
- SIEMPRE: `width:100%; height:auto` en todas las imágenes
- NUNCA: `max-height` en imágenes — achata y rompe proporciones
- NUNCA: `height` fijo en imágenes
- El ratio del polaroid (clase `mount-r-*`) controla el tamaño
- La foto respeta sus proporciones sola


- La polaroid SIEMPRE abraza la foto — nunca al revés
- NUNCA cortar la foto
- Foto horizontal Real Puerto: width:60% (inline)
- Foto a full (sp-3 Tolosa): width:100%, max-height:calc(100vh - 12rem), transform:none
- Foto vertical con texto (sp-4): img con max-height:calc(100vh - 18rem) dentro de mount-scroll2
- Fotos cuadradas/estándar: mount-scroll2 normal con width:100%; height:auto
- Siempre dar dimensiones de la foto al añadir nueva página
