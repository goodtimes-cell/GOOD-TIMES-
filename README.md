# GOOD-TIMES-
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Good Times Radio</title>
  <link href="https://fonts.googleapis.com/css2?family=Raleway:wght@400;700&display=swap" rel="stylesheet">
  <style>
    body {
      font-family: 'Raleway', sans-serif;
      background: linear-gradient(to right, #0f2027, #203a43, #2c5364);
      color: #fff;
      margin: 0;
      padding: 0;
    }
    header {
      background: rgba(0, 0, 0, 0.6);
      padding: 40px 20px;
      text-align: center;
    }
    header h1 {
      margin: 0;
      color: #ffcc00;
      font-size: 3em;
      text-shadow: 2px 2px #000;
    }
    header p {
      font-size: 1.2em;
      color: #eee;
    }
    nav {
      background: #111;
      display: flex;
      justify-content: center;
      flex-wrap: wrap;
    }
    nav a {
      color: #ffcc00;
      padding: 15px 25px;
      text-decoration: none;
      font-weight: bold;
      transition: background 0.3s;
    }
    nav a:hover {
      background: #333;
    }
    section {
      padding: 40px 20px;
      max-width: 1000px;
      margin: auto;
    }
    section h2 {
      border-bottom: 2px solid #ffcc00;
      padding-bottom: 10px;
      margin-bottom: 20px;
    }
    iframe {
      width: 100%;
      height: 400px;
      border: 3px solid #ffcc00;
      border-radius: 10px;
      margin-bottom: 30px;
    }
    ul {
      list-style: none;
      padding-left: 0;
    }
    ul li {
      padding: 10px 0;
      border-bottom: 1px solid rgba(255, 255, 255, 0.1);
    }
    ul li strong {
      color: #ffcc00;
    }
    a {
      color: #ffcc00;
    }
    a:hover {
      color: #ffffff;
    }
    footer {
      background: #000;
      text-align: center;
      padding: 15px;
      font-size: 0.9em;
      color: #aaa;
    }
  </style>
</head>
<body>
  <header>
    <h1>Good Times Radio</h1>
    <p>¡Música que te acompaña siempre!</p>
  </header>
  <nav>
    <a href="#inicio">Inicio</a>
    <a href="#vivo">En Vivo</a>
    <a href="#programacion">Programación</a>
    <a href="#contacto">Contacto</a>
  </nav>

  <section id="inicio">
    <h2>Bienvenidos a Good Times</h2>
    <p>Somos tu compañía musical ideal. Ofrecemos una mezcla vibrante de clásicos, éxitos y momentos inolvidables que te harán disfrutar cada segundo. Sintoniza y siente el ritmo.</p>
  </section>

  <section id="vivo">
    <h2>Transmisión en Vivo</h2>
    <h3>Desde YouTube</h3>
    <iframe id="youtubeFrame" allowfullscreen></iframe>

    <h3>Desde Facebook</h3>
    <iframe id="facebookFrame" allowfullscreen></iframe>
  </section>

  <section id="programacion">
    <h2>Programación</h2>
    <ul id="programacionLista"></ul>
  </section>

  <section id="contacto">
    <h2>Contacto</h2>
    <p id="email"></p>
    <p id="whatsapp"></p>
    <p>Síguenos en:</p>
    <ul>
      <li><a id="facebookLink" href="#" target="_blank">Facebook</a></li>
      <li><a id="youtubeLink" href="#" target="_blank">YouTube</a></li>
    </ul>
  </section>

  <footer>
    &copy; 2025 Good Times Radio. Todos los derechos reservados.
  </footer>

  <script>
    fetch('data.json')
      .then(response => response.json())
      .then(data => {
        document.getElementById('youtubeFrame').src = `https://www.youtube.com/embed/live_stream?channel=${data.canalYoutube}`;
        document.getElementById('facebookFrame').src = `https://www.facebook.com/plugins/video.php?href=${encodeURIComponent(data.videoFacebook)}`;

        const lista = document.getElementById('programacionLista');
        data.programacion.forEach(p => {
          const li = document.createElement('li');
          li.innerHTML = `<strong>${p.hora}:</strong> ${p.nombre}`;
          lista.appendChild(li);
        });

        document.getElementById('email').textContent = `Email: ${data.contacto.email}`;
        document.getElementById('whatsapp').textContent = `WhatsApp: ${data.contacto.whatsapp}`;
        document.getElementById('facebookLink').href = data.contacto.facebook;
        document.getElementById('youtubeLink').href = data.contacto.youtube;
      })
      .catch(error => {
        console.error('Error cargando data.json:', error);
      });
  </script>
</body>
</html>
