<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Blog Interactivo - Página Principal</title>
  
  <!-- Estilos CSS -->
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600&display=swap');

    body {
      font-family: 'Poppins', sans-serif;
      margin: 0;
      background: #fafafa;
      color: #333;
    }

    /* Encabezado y navegación */
    header {
      background: #fff;
      box-shadow: 0 2px 5px rgba(0,0,0,0.1);
      position: sticky;
      top: 0;
      z-index: 1000;
    }

    nav ul {
      list-style: none;
      margin: 0;
      padding: 0 20px;
      display: flex;
      justify-content: center;
      align-items: center;
    }

    nav ul li {
      margin: 0 15px;
    }

    nav ul li a {
      color: #333;
      text-decoration: none;
      font-weight: 500;
      transition: color 0.3s ease;
    }

    nav ul li a:hover {
      color: #007BFF;
    }

    /* Sección Hero (principal) */
    .hero {
      background: linear-gradient(135deg, #74ebd5, #ACB6E5);
      color: #fff;
      padding: 100px 20px;
      text-align: center;
    }

    .hero h1 {
      font-size: 3em;
      margin-bottom: 20px;
    }

    .hero p {
      font-size: 1.2em;
    }

    /* Secciones de contenido */
    .section {
      padding: 60px 20px;
    }

    .container {
      background: #fff;
      max-width: 800px;
      margin: 0 auto 40px auto;
      padding: 30px;
      border-radius: 10px;
      box-shadow: 0 4px 10px rgba(0,0,0,0.1);
    }

    .container h2 {
      text-align: center;
      font-size: 2em;
      margin-bottom: 30px;
    }

    /* Formularios e inputs */
    input, textarea {
      width: 100%;
      padding: 12px 15px;
      border: 1px solid #ddd;
      border-radius: 5px;
      margin: 10px 0;
      font-size: 1em;
      transition: border-color 0.3s ease;
    }

    input:focus, textarea:focus {
      border-color: #007BFF;
    }

    button {
      background: #007BFF;
      border: none;
      color: #fff;
      padding: 12px 20px;
      border-radius: 5px;
      font-size: 1em;
      cursor: pointer;
      transition: background 0.3s ease;
    }

    button:hover {
      background: #0056b3;
    }

    /* Pantalla de carga */
    #loading-screen {
      position: fixed;
      width: 100%;
      height: 100%;
      background: #fff;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      z-index: 9999;
      transition: opacity 0.5s ease;
    }

    .spinner {
      border: 6px solid #f3f3f3;
      border-top: 6px solid #007BFF;
      border-radius: 50%;
      width: 60px;
      height: 60px;
      animation: spin 1s linear infinite;
    }

    @keyframes spin {
      0% { transform: rotate(0deg); }
      100% { transform: rotate(360deg); }
    }

    .hidden {
      opacity: 0;
      pointer-events: none;
    }

    /* Pie de página */
    footer {
      background: #333;
      color: #fff;
      text-align: center;
      padding: 20px;
    }

    /* Pelota azul animada (movimiento sutil) */
    .ball {
      width: 40px;
      height: 40px;
      background: radial-gradient(circle, #007BFF, #0056b3);
      border-radius: 50%;
      position: fixed;
      top: 100px;
      left: 100px;
      animation: float 3s ease-in-out infinite;
      z-index: 100;
    }

    @keyframes float {
      0% { transform: translate(0, 0); }
      50% { transform: translate(20px, 20px); }
      100% { transform: translate(0, 0); }
    }

    /* Galería de Revistas */
    .image-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
      gap: 15px;
    }

    .image-grid img {
      width: 100%;
      border-radius: 10px;
      transition: transform 0.3s ease;
    }

    .image-grid img:hover {
      transform: scale(1.05);
    }
  </style>
</head>
<body>
  <!-- Pantalla de carga -->
  <div id="loading-screen">
    <div class="spinner"></div>
    <p>Cargando...</p>
  </div>

  <header>
    <nav>
      <ul>
        <li><a href="#">Inicio</a></li>
        <li><a href="#blog">Blog</a></li>
        <li><a href="#revistas">Revistas</a></li>
        <li><a href="#perfil">Perfil</a></li>
      </ul>
    </nav>
  </header>

  <section class="hero">
    <h1>Bienvenido a Nuestro Blog</h1>
    <p>Descubre contenido exclusivo y participa en debates apasionantes.</p>
  </section>

  <!-- Pelota azul animada -->
  <div class="ball"></div>

  <section id="blog" class="section">
    <div class="container">
      <h2>Foro de Debate</h2>
      <form id="newPost">
        <input type="text" id="postTitle" placeholder="Título del debate" required>
        <textarea id="postContent" placeholder="Escribe tu mensaje..." required></textarea>
        <button type="submit">Publicar</button>
      </form>
      <div id="posts"></div>
    </div>
  </section>

  <section id="revistas" class="section">
    <div class="container gallery">
      <h2>Revistas Recientes</h2>
      <div class="image-grid">
        <img src="https://via.placeholder.com/150" alt="Revista 1">
        <img src="https://via.placeholder.com/150" alt="Revista 2">
        <img src="https://via.placeholder.com/150" alt="Revista 3">
      </div>
    </div>
  </section>

  <section id="perfil" class="section">
    <div class="container perfil-container">
      <h2>Perfil de Usuario</h2>
      <div id="user-info"></div>
      <form id="login-form">
        <input type="email" id="email" placeholder="Correo electrónico" required>
        <input type="password" id="password" placeholder="Contraseña" required>
        <button type="submit">Iniciar Sesión</button>
      </form>
      <button id="logout" style="display: none;">Cerrar Sesión</button>
    </div>
  </section>

  <footer>
    <p>&copy; 2025 Blog Interactivo. Todos los derechos reservados.</p>
  </footer>

  <script>
    document.addEventListener("DOMContentLoaded", function () {
      // Ocultar la pantalla de carga
      setTimeout(() => {
        document.getElementById("loading-screen").classList.add("hidden");
      }, 800);

      /* ---------- Foro (Chat) ---------- */
      const newPostForm = document.getElementById("newPost");
      const postsContainer = document.getElementById("posts");
      if (newPostForm) {
        newPostForm.addEventListener("submit", function (e) {
          e.preventDefault();
          const title = document.getElementById("postTitle").value;
          const content = document.getElementById("postContent").value;
          const postHTML = `<div style="margin-bottom:20px; text-align:left;"><h3>${title}</h3><p>${content}</p></div>`;
          postsContainer.innerHTML += postHTML;
          newPostForm.reset();
        });
      }

      /* ---------- Gestión de Usuario (Perfil) ---------- */
      const loginForm = document.getElementById("login-form");
      const logoutButton = document.getElementById("logout");
      const userInfo = document.getElementById("user-info");

      function setCookie(name, value, days) {
        let expires = "";
        if (days) {
          let date = new Date();
          date.setTime(date.getTime() + days * 24 * 60 * 60 * 1000);
          expires = "; expires=" + date.toUTCString();
        }
        document.cookie = name + "=" + value + expires + "; path=/";
      }

      function getCookie(name) {
        let nameEQ = name + "=";
        let ca = document.cookie.split(";");
        for (let c of ca) {
          c = c.trim();
          if (c.indexOf(nameEQ) === 0) return c.substring(nameEQ.length);
        }
        return null;
      }

      function eraseCookie(name) {
        document.cookie = name + "=; Max-Age=-99999999;";
      }

      function checkUserSession() {
        let savedUser = getCookie("userEmail");
        if (savedUser)
