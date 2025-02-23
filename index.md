<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Grupo ZION</title>
    <style>
        /* Global Styles */
        body {
            font-family: Arial, Helvetica, sans-serif;
            background: url('Dune.png') no-repeat center center fixed;
            background-size: cover;
            color: #333;
            margin: 0;
            padding: 0;
            line-height: 1.6;
        }

        h1, h2, h3, p {
            margin: 0;
        }

        a {
            text-decoration: none;
            color: #333;
        }

        /* Background overlay for readability */
        .overlay {
            background: rgba(255, 255, 255, 0.8);
            width: 100%;
            height: 100%;
            position: fixed;
            top: 0;
            left: 0;
            z-index: -1;
        }

        /* Header */
        header {
            background-color: #000;
            color: #fff;
            padding: 20px 0;
            text-align: center;
        }

        header h1 {
            font-size: 36px;
        }

        /* Navigation */
        nav {
            background-color: #333;
            padding: 10px;
            text-align: center;
        }

        nav a {
            margin: 0 15px;
            color: #fff;
            font-size: 18px;
            padding: 8px 15px;
            border-radius: 4px;
        }

        nav a:hover {
            background-color: #444;
        }

        /* Main Layout */
        .container {
            padding: 20px;
            display: flex;
            gap: 20px;
        }

        .news-sidebar {
            flex: 1;
            background-color: #f4f4f4;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
        }

        .news-sidebar ul {
            list-style: none;
            padding: 0;
        }

        .news-sidebar li {
            margin-bottom: 10px;
        }

        .content {
            flex: 3;
            display: flex;
            flex-direction: column;
            gap: 20px;
        }

        .section {
            display: flex;
            gap: 20px;
            align-items: center;
        }

        .video-container {
            flex: 2;
        }

        .video-container video {
            width: 100%;
            display: block;
        }

        .text-box {
            flex: 1;
            background-color: #f4f4f4;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
        }

        /* Footer */
        footer {
            background-color: #333;
            color: #fff;
            text-align: center;
            padding: 10px;
        }

        footer p {
            font-size: 14px;
        }

        /* Responsive */
        @media (max-width: 768px) {
            .container {
                flex-direction: column;
            }
            .section {
                flex-direction: column;
            }
        }
    </style>
    <script>
        async function fetchNews() {
            try {
                const response = await fetch('https://api.rss2json.com/v1/api.json?rss_url=https://news.google.com/rss/search?q=sostenibilidad&hl=es&gl=ES&ceid=ES:es');
                const data = await response.json();
                
                if (data.items) {
                    let newsList = '';
                    data.items.slice(0, 5).forEach(item => {
                        newsList += `<li><a href="${item.link}" target="_blank">${item.title}</a></li>`;
                    });
                    document.getElementById('news-feed').innerHTML = newsList;
                } else {
                    document.getElementById('news-feed').innerHTML = '<li>No se encontraron noticias.</li>';
                }
            } catch (error) {
                console.error('Error al obtener noticias:', error);
                document.getElementById('news-feed').innerHTML = '<li>Error al cargar noticias.</li>';
            }
        }
        window.onload = fetchNews;
    </script>
</head>
<body>

    <!-- Capa para mejorar la legibilidad del contenido sobre la imagen -->
    <div class="overlay"></div>

    <header>
        <h1>Grupo ZION</h1>
        <p>Transformando el futuro con tecnología</p>
    </header>

    <nav>
        <a href="#">Inicio</a>
        <a href="nosotros.html">Nosotros</a>
        <a href="galeria.html">Galería</a>
        <a href="contactos.html">Contacto</a>
    </nav>

    <div class="container">
        <aside class="news-sidebar">
            <h2>Agenda 2030</h2>
            <ul id="news-feed">
                <li>Cargando noticias...</li>
            </ul>
        </aside>
        
        <div class="content">
            <div class="section">
                <div class="video-container">
                    <video src="video1.mp4" autoplay muted loop></video>
                </div>
                <div class="text-box">
                    <h2>Nuestra Visión</h2>
                    <p>Innovación y tecnología para un futuro mejor.</p>
                </div>
            </div>
    
            <div class="section">
                <div class="text-box">
                    <h2>Nuestros Proyectos</h2>
                    <p>Descubre cómo estamos transformando la industria.</p>
                </div>
                <div class="video-container">
                    <video src="video2.mp4" autoplay muted loop></video>
                </div>
            </div>
        </div>
    </div>

    <footer>
        <p>&copy; 2025 Grupo ZION. Todos los derechos reservados.</p>
    </footer>

</body>
</html>
