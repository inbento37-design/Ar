<!doctype html>
<html lang="es">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Acceso Exclusivo</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <style>
    * { font-family: Arial, sans-serif; }
  </style>
</head>
<body class="bg-gray-50 text-gray-900">

  <header class="bg-white shadow p-4 flex justify-between items-center">
    <h1 class="text-xl font-bold">🎯 Acceso Exclusivo</h1>
    <button id="open-sub-modal" class="bg-red-600 text-white px-4 py-2 rounded-lg font-semibold">Suscribirse</button>
  </header>

  <main class="max-w-2xl mx-auto p-6 text-center">
    <h2 class="text-2xl font-bold mb-4">Sigue los pasos para acceder</h2>
    <p class="mb-6">Debes suscribirte, dar like y verificar antes de acceder al contenido.</p>
    <button id="open-gate" class="bg-red-600 text-white px-6 py-3 rounded-lg font-semibold">Comenzar</button>
  </main>

  <!-- Modal -->
  <div id="subscribe-modal" class="fixed inset-0 bg-black/70 hidden z-50 flex items-center justify-center">
    <div class="bg-white rounded-xl shadow-xl max-w-md w-full p-6 text-center">
      <h3 class="text-xl font-bold mb-2">Verificación de pasos</h3>
      <p class="text-sm text-gray-600 mb-4">Completa cada paso para desbloquear el contenido.</p>

      <!-- Paso 1 -->
      <div id="like-step">
        <button id="open-video" class="bg-red-600 text-white px-5 py-3 rounded-lg font-semibold">Dar like al video</button>
      </div>

      <!-- Paso 2 -->
      <div id="robot-check" class="hidden mt-4">
        <button id="not-robot" class="px-5 py-3 rounded-lg border-2 border-gray-500 font-semibold">No soy un robot</button>
      </div>

      <!-- Paso 3 -->
      <div id="progress-area" class="hidden mt-4">
        <p class="text-sm mb-2">Espera 7 segundos...</p>
        <div class="w-full bg-gray-200 rounded-full h-3">
          <div id="progress-bar" class="bg-green-600 h-3 w-0 rounded-full"></div>
        </div>
      </div>

      <!-- Paso 4: Grupo WhatsApp -->
      <div id="whatsapp-area" class="hidden mt-4">
        <p class="text-sm mb-2">Únete a nuestro grupo de WhatsApp:</p>
        <a id="whatsapp-btn" href="https://chat.whatsapp.com/IS0qnB7oGtJJaF0e9nR1Ke?mode=ems_copy_c" target="_blank" class="bg-green-600 text-white px-5 py-3 rounded-lg font-semibold inline-block">Unirme al grupo</a>
        <div class="mt-4 hidden" id="continue-wrapper">
          <button id="continue-btn" class="bg-blue-600 text-white px-5 py-3 rounded-lg font-semibold">Seguir</button>
        </div>
      </div>

      <!-- Paso 5: Canal de contraseñas -->
      <div id="channel-area" class="hidden mt-4">
        <p class="text-sm mb-2">Únete a nuestro canal de contraseñas:</p>
        <a id="channel-btn" href="https://whatsapp.com/channel/0029Vb7eMWgLSmbj2TiK7m0y" target="_blank" class="bg-purple-600 text-white px-5 py-3 rounded-lg font-semibold inline-block">Unirme al canal</a>
        <div class="mt-4 hidden" id="channel-continue-wrapper">
          <button id="channel-continue-btn" class="bg-blue-600 text-white px-5 py-3 rounded-lg font-semibold">Seguir</button>
        </div>
      </div>

      <!-- Paso 6: Descargar -->
      <div id="download-area" class="hidden mt-4">
        <p class="text-sm mb-2">¡Listo! Ahora puedes descargar:</p>
        <a id="download-link" href="#" target="_blank" class="bg-green-600 text-white px-5 py-3 rounded-lg font-semibold inline-block">Descargar ahora</a>
      </div>
    </div>
  </div>

  <script>
    // ==========================================================
    // CONFIGURACIÓN PERSONALIZABLE
    // ==========================================================

    // ✅ Canal de YouTube
    const CHANNEL_URL = "https://www.youtube.com/@jk-trickxitxx2625";

    // 🎥 Video que deben dar like
    const VIDEO_URL = "https://youtu.be/QJwx8fBnkz4?si=qXBtCZV5wUbRqt1m";

    // 💬 Grupo de WhatsApp
    const WHATSAPP_URL = "https://chat.whatsapp.com/IS0qnB7oGtJJaF0e9nR1Ke?mode=ems_copy_c";

    // 🔐 Canal de contraseñas
    const CHANNEL_WHATSAPP_URL = "https://whatsapp.com/channel/0029Vb7eMWgLSmbj2TiK7m0y";

    // ==========================================================
    // 🟩 AQUÍ DEBES PONER TU ENLACE DE DESCARGA DE MEDIAFIRE 🟩
    //
    // 👉 Ejemplo:
    // const DOWNLOAD_URL = "https://www.mediafire.com/file/XXXXX/archivo.zip/file";
    //
    // Pega tu enlace de descarga en esta línea ↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓
    const DOWNLOAD_URL = "https://www.mediafire.com/file/ajrpcnwh5m2056j/AIMBOT+BRASILEÑO+V4🇧🇷.zip/file";
    // ↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑
    // ==========================================================

    // Elementos del DOM
    const modal = document.getElementById('subscribe-modal');
    const openGateBtn = document.getElementById('open-gate');
    const openVideoBtn = document.getElementById('open-video');
    const robotCheck = document.getElementById('robot-check');
    const notRobotBtn = document.getElementById('not-robot');
    const progressArea = document.getElementById('progress-area');
    const progressBar = document.getElementById('progress-bar');
    const whatsappArea = document.getElementById('whatsapp-area');
    const whatsappBtn = document.getElementById('whatsapp-btn');
    const continueWrapper = document.getElementById('continue-wrapper');
    const continueBtn = document.getElementById('continue-btn');
    const channelArea = document.getElementById('channel-area');
    const channelBtn = document.getElementById('channel-btn');
    const channelContinueWrapper = document.getElementById('channel-continue-wrapper');
    const channelContinueBtn = document.getElementById('channel-continue-btn');
    const downloadArea = document.getElementById('download-area');
    const downloadLink = document.getElementById('download-link');

    function showModal(){ modal.classList.remove('hidden'); }

    openGateBtn.addEventListener('click', () => {
      showModal();
      window.open(CHANNEL_URL, '_blank');
    });

    document.getElementById('open-sub-modal').addEventListener('click', () => {
      showModal();
      window.open(CHANNEL_URL, '_blank');
    });

    openVideoBtn.addEventListener('click', () => {
      window.open(VIDEO_URL, '_blank');
      robotCheck.classList.remove('hidden');
    });

    notRobotBtn.addEventListener('click', () => {
      robotCheck.classList.add('hidden');
      progressArea.classList.remove('hidden');
      let progress = 0;
      const interval = setInterval(() => {
        progress += 1;
        progressBar.style.width = progress + '%';
        if(progress >= 100){
          clearInterval(interval);
          progressArea.classList.add('hidden');
          whatsappArea.classList.remove('hidden');
        }
      }, 70);
    });

    whatsappBtn.addEventListener('click', () => {
      continueWrapper.classList.remove('hidden');
    });

    continueBtn.addEventListener('click', () => {
      whatsappArea.classList.add('hidden');
      channelArea.classList.remove('hidden');
    });

    channelBtn.addEventListener('click', () => {
      channelContinueWrapper.classList.remove('hidden');
    });

    channelContinueBtn.addEventListener('click', () => {
      channelArea.classList.add('hidden');
      downloadArea.classList.remove('hidden');
    });

    // Acción del botón "Descargar ahora"
    downloadLink.addEventListener('click', (e) => {
      e.preventDefault();
      if (DOWNLOAD_URL === "https://www.mediafire.com/file/ajrpcnwh5m2056j/AIMBOT+BRASILEÑO+V4🇧🇷.zip/file") {
        alert("⚠️ Debes colocar tu enlace de descarga en el código (const DOWNLOAD_URL).");
      } else {
        window.open(DOWNLOAD_URL, '_blank');
      }
    });
  </script>

</body>
</html>
