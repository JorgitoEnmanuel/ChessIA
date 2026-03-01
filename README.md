<!DOCTYPE html>
<html>
<head>
    <title>Mentor de Ajedrez IA</title>
    <script src="https://telegram.org/js/telegram-web-app.js"></script>
    <link rel="stylesheet" href="https://unpkg.com/@chrisoakman/chessboardjs@1.0.0/dist/chessboard-1.0.0.min.css">
    <script src="https://code.jquery.com/jquery-3.5.1.min.js"></script>
    <script src="https://unpkg.com/chess.js@0.10.3/chess.js"></script>
    <script src="https://unpkg.com/@chrisoakman/chessboardjs@1.0.0/dist/chessboard-1.0.0.min.js"></script>
    <style>
        body { background: #1a1a1a; color: white; font-family: sans-serif; text-align: center; }
        #board { width: 350px; margin: 20px auto; }
        #status { padding: 15px; background: #333; border-radius: 10px; margin: 10px; min-height: 50px; }
        .loading { color: #f1c40f; }
    </style>
</head>
<body>
    <h3>?? Mentor Gemini</h3>
    <div id="status">Haz tu movimiento para recibir consejo...</div>
    <div id="board"></div>

    <script>
        var board = null;
        var game = new Chess();
        var $status = $('#status');

        function onDrop (source, target) {
            var move = game.move({ from: source, to: target, promotion: 'q' });
            if (move === null) return 'snapback';

            // ENVIAR A MAKE.COM
            $status.html('<span class="loading">Pensando...</span>');
            
            fetch('TU_URL_DE_WEBHOOK_DE_MAKE', {
                method: 'POST',
                headers: { 'Content-Type': 'application/json' },
                body: JSON.stringify({
                    move: move.san,
                    fen: game.fen(),
                    user: Telegram.WebApp.initDataUnsafe.user?.first_name || "Jugador"
                })
            })
            .then(res => res.json())
            .then(data => {
                $status.html(data.respuesta); // Aquí mostramos lo que dice Gemini
                if(data.movimiento_ia) {
                    game.move(data.movimiento_ia);
                    board.position(game.fen());
                }
            });
        }

        var config = { draggable: true, position: 'start', onDrop: onDrop };
        board = Chessboard('board', config);
        Telegram.WebApp.ready();
    </script>
</body>
</html>
