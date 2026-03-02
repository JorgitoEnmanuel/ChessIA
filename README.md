<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Mini App Ajedrez</title>
  <style>
    body {
      margin: 0;
      padding: 0;
      background: #f0f0f0;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh; /* ocupa toda la pantalla */
    }
    #board {
      width: 90vw;   /* ancho relativo a la pantalla */
      max-width: 500px; /* límite máximo para no desbordar */
    }
  </style>
  <!-- Librería Chessboard.js -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/chessboard-js/1.0.0/chessboard-1.0.0.min.css" />
  <script src="https://cdnjs.cloudflare.com/ajax/libs/chessboard-js/1.0.0/chessboard-1.0.0.min.js"></script>
  <!-- Telegram WebApp API -->
  <script src="https://telegram.org/js/telegram-web-app.js"></script>
</head>
<body>
  <div id="board"></div>

  <script>
    // Inicializar tablero
    var board = Chessboard('board', {
      position: 'start', // posición inicial
      draggable: true    // permitir arrastrar piezas
    });

    // Ajustar tamaño según la pantalla del móvil
    function resizeBoard() {
      let height = Telegram.WebApp.viewportHeight; // altura disponible
      let width = Telegram.WebApp.viewportWidth;   // ancho disponible
      document.getElementById('board').style.width = Math.min(width * 0.9, 500) + 'px';
      board.resize();
    }

    // Expandir mini app a pantalla completa
    Telegram.WebApp.expand();

    // Ajustar tablero al cargar
    resizeBoard();

    // Ajustar tablero si cambia el tamaño de la pantalla
    Telegram.WebApp.onEvent('viewportChanged', resizeBoard);
  </script>
</body>
</html>
