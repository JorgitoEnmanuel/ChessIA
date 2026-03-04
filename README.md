# ♟️ AI Chess Tutor - Prototipo

Este es un tutor de ajedrez interactivo basado en la web que utiliza inteligencia artificial para analizar posiciones y ofrecer consejos pedagógicos en tiempo real. Combina la potencia de un motor de ajedrez local con la capacidad narrativa de modelos de lenguaje a través de automatización.

## 🚀 Características

- **Tablero Interactivo:** Construido con `chessboard.js` y `chess.js` para una experiencia de juego fluida.
- **Motor Stockfish Local:** Integración de `stockfish.js` mediante Web Workers para evaluación inmediata de la posición.
- **Modo Edición:** Herramienta para configurar posiciones personalizadas (estudios o finales) simplemente arrastrando piezas.
- **Mentor IA:** Integración con **Make.com** para enviar datos de la partida y recibir explicaciones tácticas y sugerencias de mejora.
- **Voz y Chat:** Soporte para comandos de voz y respuestas interactivas.

## 🛠️ Stack Tecnológico

- **Frontend:** HTML5, CSS3 (Flexbox), JavaScript (jQuery).
- **Lógica de Ajedrez:** [Chess.js](https://github.com/jhlywa/chess.js) y [Chessboard.js](https://chessboardjs.com/).
- **Motor de Análisis:** [Stockfish.js](https://github.com/nmrugg/stockfish.js).
- **Backend/Automatización:** Webhooks de Make.com.

## 📦 Instalación y Uso Local

Debido a que el motor Stockfish utiliza *Web Workers*, los navegadores bloquean su ejecución si abres el archivo directamente (`file://`).

1. **Clona el repositorio:**
   ```bash
   git clone [https://github.com/tu-usuario/nombre-del-repo.git](https://github.com/tu-usuario/nombre-del-repo.git)
