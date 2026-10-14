# clak

Herramientas para que un agente edite mis videos a partir de mi voz. Yo grabo el audio; clak hace el resto por etapas y yo apruebo cada una: cortes, animaciones, transiciones, sonido, subtítulos, grabación de pantalla y diseño.

El nombre viene del sonido de la claqueta.

## Principio

La voz manda. El audio grabado es la línea de tiempo: cada animación, corte, efecto y subtítulo se amarra a la frase que lo dispara.

## Qué videos

- Video corto vertical hablando a cámara.
- Grabaciones de pantalla: demos y tutoriales.
- Piezas animadas sin cámara, con voz.

## De dónde sale

El video de presentación de Nodus (`~/dev/personal/nodus/pitch/`) ya hizo casi todo esto para un solo video:

| Parte | Cómo lo hizo |
|---|---|
| Diseño | Escenas animadas en una ruta `/pitch` de la app, con los componentes y tokens de Nodus |
| Tiempos | Whisper (stable-ts) saca cada palabra con su segundo; `anclar.ts` pone cada paso a la hora de su frase |
| Render | `render.ts`: Chromium sin ventana, cuadro por cuadro, determinista; ffmpeg junta los cuadros |
| Sonido | `sonido.py`: cama y efectos sintetizados, colgados de los tiempos de la voz |
| Demo | `grabar.ts` recorre la app sola con un puntero dibujado; `demo-montar.ts` corta cada toma a su frase |
| Subtítulos | `subtitulos.ts`: en inglés, quemados sin tapar la pantalla, y SRT en inglés y español |

clak saca ese pipeline de Nodus para que sirva en cualquier video.

## Estado

Idea. Falta definir el alcance con una ronda de preguntas: forma (CLI, MCP o ambas), renderizar por código o manejar CapCut o DaVinci, cómo se guarda la base de diseño, y cuál es la primera versión.

Uso personal primero; después repo público.
