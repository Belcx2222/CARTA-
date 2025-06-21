<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Carta de Amor</title>
  <style>
    body {
      background-color: #ffe6f0;
      background-image: url('https://i.pinimg.com/originals/0c/8e/f8/0c8ef82f10cf92b3ce64586d99b9aa68.gif');
      background-size: 200px;
      background-repeat: repeat;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: start;
      height: 100vh;
      margin: 0;
      font-family: 'Courier New', monospace;
      overflow: hidden;
    }

    .peluche {
      width: 120px;
      margin-top: 20px;
      z-index: 2;
    }

    .marco {
      border: 5px dashed #ff85a2;
      border-radius: 20px;
      padding: 25px;
      background-color: rgba(255, 255, 255, 0.9);
      box-shadow: 0 0 15px rgba(255, 105, 180, 0.4);
    }

    .carta-container {
      perspective: 1000px;
      margin-top: 20px;
    }

    .carta {
      width: 400px;
      height: 300px;
      position: relative;
      transform-style: preserve-3d;
      transition: transform 1s;
      cursor: pointer;
    }

    .carta.abierta {
      transform: rotateY(180deg);
    }

    .cara, .contenido {
      position: absolute;
      width: 100%;
      height: 100%;
      backface-visibility: hidden;
      border-radius: 10px;
    }

    .cara {
      background-color: #ffb6c1;
      display: flex;
      justify-content: center;
      align-items: center;
      font-size: 24px;
      font-weight: bold;
      color: white;
      box-shadow: 0 4px 8px rgba(0,0,0,0.2);
    }

    .contenido {
      background-color: white;
      transform: rotateY(180deg);
      padding: 20px;
      box-sizing: border-box;
      text-align: center;
      color: #d63384;
      font-size: 18px;
      line-height: 1.4;
      box-shadow: 0 4px 8px rgba(0,0,0,0.2);
      overflow-y: auto;
    }

    .corazon {
      font-size: 30px;
      animation: latir 1s infinite;
    }

    @keyframes latir {
      0%,100% { transform: scale(1); }
      50% { transform: scale(1.2); }
    }

    /* "Te amo" animaciones */
    .teamo {
      position: absolute;
      color: #ff3f7f;
      font-size: 24px;
      font-weight: bold;
      animation: flotar 3s ease-in forwards;
      pointer-events: none;
      text-shadow: 0 0 5px #fff;
    }

    @keyframes flotar {
      0% {
        opacity: 1;
        transform: translateY(0) scale(1);
      }
      100% {
        opacity: 0;
        transform: translateY(-300px) scale(1.5);
      }
    }
  </style>
</head>
<body>

  <!-- Peluche animado -->
  <img class="peluche" src="https://media.tenor.com/45Ds0MiHDD0AAAAi/teddy-bear-love-you.gif" alt="Peluche">

  <div class="marco">
    <div class="carta-container">
      <div class="carta" onclick="abrirCarta(this)">
        <div class="cara">💌 Haz clic para abrir</div>
        <div class="contenido">
          <p>
            Amor mío,<br><br>
            Desde que llegaste a mi vida todo cambió.<br>
            Eres mi alegría, mi paz y mi motivo de sonreír.<br>
            Gracias por cada mirada, cada palabra, cada abrazo.<br>
            Eres más de lo que soñé.<br><br>
            Te amo con todo mi corazón.<br><br>
            <span class="corazon">❤️</span>
          </p>
        </div>
      </div>
    </div>
  </div>

  <!-- YouTube embed oculto -->
  <iframe id="ytplayer" style="display:none;" src="https://www.youtube.com/embed/Xl_dsORo4E0?enablejsapi=1" allow="autoplay"></iframe>

  <script>
    let player;
    function onYouTubeIframeAPIReady() {
      player = new YT.Player('ytplayer', {});
    }

    function abrirCarta(elem) {
      elem.classList.toggle('abierta');
      lanzarTeAmo();
      if (player && player.playVideo) player.playVideo();
    }

    function lanzarTeAmo() {
      for (let i = 0; i < 20; i++) {
        const t = document.createElement('div');
        t.className = 'teamo';
        t.innerText = 'Te amo';
        t.style.left = Math.random() * window.innerWidth + 'px';
        t.style.top = (Math.random() * 100 + 400) + 'px';
        t.style.animationDelay = Math.random() + 's';
        document.body.appendChild(t);
        setTimeout(() => t.remove(), 3000);
      }
    }
  </script>
  <script src="https://www.youtube.com/iframe_api"></script>

</body>
</html>
