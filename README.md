<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Proyecto Escolar - Puente Negro</title>
    <!-- Estilos basados en la paleta de colores de tus imágenes -->
    <style>
        :root {
            --bg-color: #d0f0ed; /* Color turquesa claro de tu segunda imagen */
            --primary-dark: #006666; /* Color oscuro para iconos y acentos */
            --accent-color: #008080;
            --text-main: #2b3e3e;
            --white: #ffffff;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: var(--bg-color);
            color: var(--text-main);
            margin: 0;
            padding: 20px;
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        header {
            text-align: center;
            margin-bottom: 30px;
        }

        h1 {
            color: var(--primary-dark);
            margin-bottom: 5px;
        }

        p.subtitle {
            font-size: 1.1rem;
            color: var(--accent-color);
            margin-top: 0;
        }

        .container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 20px;
            width: 100%;
            max-width: 900px;
        }

        /* Tarjeta de Estudiante inspirada en tu segunda imagen */
        .card {
            background-color: var(--white);
            border-radius: 15px;
            padding: 25px;
            box-shadow: 0 4px 15px rgba(0, 102, 102, 0.15);
            display: flex;
            flex-direction: column;
            align-items: center;
            text-align: center;
            transition: transform 0.2s ease;
        }

        .card:hover {
            transform: translateY(-5px);
        }

        .avatar-container {
            width: 90px;
            height: 90px;
            background-color: var(--bg-color);
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            margin-bottom: 15px;
            border: 3px solid var(--primary-dark);
        }

        /* Ícono de usuario idéntico al de tu captura */
        .avatar-icon {
            width: 50px;
            height: 50px;
            fill: var(--primary-dark);
        }

        .student-name {
            font-size: 1.3rem;
            font-weight: bold;
            color: var(--primary-dark);
            margin: 5px 0;
        }

        .category-tag {
            background-color: var(--bg-color);
            color: var(--primary-dark);
            padding: 5px 12px;
            border-radius: 20px;
            font-size: 0.9rem;
            font-weight: 600;
            margin-bottom: 15px;
        }

        .description {
            font-size: 0.95rem;
            color: #555;
            margin-bottom: 20px;
            line-height: 1.4;
        }

        /* Botón de voz interactivo */
        .btn-voice {
            background-color: var(--primary-dark);
            color: var(--white);
            border: none;
            padding: 10px 20px;
            border-radius: 25px;
            font-size: 0.95rem;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 8px;
            transition: background-color 0.2s;
        }

        .btn-voice:hover {
            background-color: var(--accent-color);
        }

        footer {
            margin-top: 40px;
            text-align: center;
            font-size: 0.9rem;
            color: var(--primary-dark);
        }
    </style>
</head>
<body>

    <header>
        <h1>Proyecto Escolar: El Puente Negro</h1>
        <p class="subtitle">Escanea los perfiles de los estudiantes e investiga su historia</p>
    </header>

    <div class="container" id="students-container">
        <!-- Estudiante 1 -->
        <div class="card">
            <div class="avatar-container">
                <svg class="avatar-icon" viewBox="0 0 24 24">
                    <path d="M12 12c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm0 2c-2.67 0-8 1.34-8 4v2h16v-2c0-2.66-5.33-4-8-4z"/>
                </svg>
            </div>
            <div class="student-name">María Espino</div>
            <div class="category-tag">Historia y Origen</div>
            <div class="description">
                El Puente Negro es uno de los monumentos históricos más emblemáticos de nuestra región, construido a principios del siglo XX para mejorar las vías de comunicación ferroviaria.
            </div>
            <button class="btn-voice" onclick="leerTexto('El Puente Negro es uno de los monumentos históricos más emblemáticos de nuestra región, construido a principios del siglo XX para mejorar las vías de comunicación ferroviaria.')">
                🔊 Escuchar Voz
            </button>
        </div>

        <!-- Estudiante 2 -->
        <div class="card">
            <div class="avatar-container">
                <svg class="avatar-icon" viewBox="0 0 24 24">
                    <path d="M12 12c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm0 2c-2.67 0-8 1.34-8 4v2h16v-2c0-2.66-5.33-4-8-4z"/>
                </svg>
            </div>
            <div class="category-tag">Arquitectura y Estructura</div>
            <div class="student-name">Colaborador 2</div>
            <div class="description">
                Su estructura destaca por el uso masivo de acero remachado de la época industrial, diseñado con vigas de celosía que garantizaban una enorme resistencia sobre el río.
            </div>
            <button class="btn-voice" onclick="leerTexto('Su estructura destaca por el uso masivo de acero remachado de la época industrial, diseñado con vigas de celosía que garantizaban una enorme resistencia sobre el río.')">
                🔊 Escuchar Voz
            </button>
        </div>
    </div>

    <footer>
        <p>Proyecto Escolar 2026 - Creado para GitHub Pages</p>
    </footer>

    <!-- Script para reproducir la voz del estudiante -->
    <script>
        function leerTexto(texto) {
            if ('speechSynthesis' in window) {
                // Detener cualquier audio previo
                window.speechSynthesis.cancel();
                
                const utterance = new SpeechSynthesisUtterance(texto);
                utterance.lang = 'es-ES'; // Configurado en español
                utterance.rate = 1.0;     // Velocidad normal
                
                window.speechSynthesis.speak(utterance);
            } else {
                alert("Lo siento, tu navegador no soporta la reproducción de voz.");
            }
        }
    </script>
</body>
</html>
