# DUB²BEAT PHOTOGRAPHY — Notas de cambios

## Estructura
- Todo en un solo `index.html` — portada + álbum integrados
- No hay CSS separado, todo inline en el HTML

## Álbum
- Nuevo layout: **dos polaroids por página** sobre fondo textura diario
- Spines izquierdo y derecho en las páginas del álbum (igual que portada)
- PÁG. 1: Fuego, Adicción y Muerte (izquierda) + Real Puerto Hispano Americano (derecha)
- Foto horizontal (Real Puerto): ancho 60% para respetar proporciones
- Foto cuadrada (Fuego): ancho estándar `min(48%, ...)`
- Texto de cada foto dentro del polaroid, en Caveat azul bic / rojo destacado

## Navegación
- Por defecto abre en la **última página** (orden diario, lo más reciente primero)
- Botón **⇄ CRONOLÓGICO** en portada y en álbum — cambia al orden tradicional
- Botón sincronizado entre portada y álbum
- Footer álbum: ✕ PORTADA · ▶ DIAPOSITIVAS · ◂ ANTERIOR · PÁG. X/X · SIGUIENTE ▸ · ⇄ CRONOLÓGICO
- Footer portada: ▶ DIAPOSITIVAS · DUB²BEAT · PÁG. 1 ▸ · ⇄ CRONOLÓGICO
- DIAPOSITIVAS desde portada abre álbum y arranca slideshow (13 seg por página)

## Para añadir páginas
- Duplicar el bloque `<div class="spread" id="sp-N">` con el nuevo N
- Actualizar `const TOTAL=N` en el JS
- La nueva página será la primera en abrirse (orden diario)
