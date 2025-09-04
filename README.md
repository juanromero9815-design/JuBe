<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>Jogo do Amor 💖</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: linear-gradient(135deg, #ff9a9e, #fecfef);
      text-align: center;
      padding: 40px;
      overflow: hidden;
    }
    h1 {
      color: #fff;
      text-shadow: 2px 2px 5px #d63384;
    }
    .grid {
      display: grid;
      grid-template-columns: repeat(4, 80px);
      grid-gap: 15px;
      justify-content: center;
      margin-top: 30px;
    }
    .heart {
      font-size: 40px;
      cursor: pointer;
      transition: transform 0.2s;
    }
    .heart:hover {
      transform: scale(1.3);
    }
    #mensagem {
      margin-top: 30px;
      font-size: 22px;
      font-weight: bold;
      color: #fff;
      text-shadow: 2px 2px 5px #ff4d6d;
    }
    .floating-heart {
      position: fixed;
      font-size: 25px;
      animation: subir 4s linear forwards;
      pointer-events: none;
    }
    @keyframes subir {
      0% { transform: translateY(0) scale(1); opacity: 1; }
      100% { transform: translateY(-600px) scale(1.5); opacity: 0; }
    }
  </style>
</head>
<body>
  <h1>💘 Encontre o Tesouro do Amor 💘</h1>
  <p>Clique nos corações para descobrir a surpresa!</p>
  
  <div class="grid" id="grid"></div>
  
  <div id="mensagem"></div>
  
  <script>
    const grid = document.getElementById("grid");
    const mensagem = document.getElementById("mensagem");

    // cria 12 corações
    let coracoes = [];
    for (let i = 0; i < 12; i++) {
      let heart = document.createElement("div");
      heart.innerHTML = "❤️";
      heart.classList.add("heart");
      heart.dataset.index = i;
      heart.onclick = clicarCoracao;
      coracoes.push(heart);
      grid.appendChild(heart);
    }

    // escolhe 1 coração secreto
    const tesouro = Math.floor(Math.random() * 12);

    function clicarCoracao(e) {
      const index = e.target.dataset.index;
      if (index == tesouro) {
        mensagem.innerHTML = "🎉 Parabéns Gabrielle! 🎉<br>Você encontrou o maior tesouro: <br><span style='font-size:26px;'>💖 O meu amor por você! 💖</span>";
        soltarCoracoes();
      } else {
        mensagem.innerHTML = "Esse não é o coração certo... tente outro 💕";
        e.target.style.opacity = "0.3";
        e.target.style.pointerEvents = "none";
      }
    }

    // solta vários corações animados pela tela
    function soltarCoracoes() {
      for (let i = 0; i < 30; i++) {
        let heart = document.createElement("div");
        heart.classList.add("floating-heart");
        heart.innerHTML = "💖";
        heart.style.left = Math.random() * window.innerWidth + "px";
        heart.style.bottom = "0px";
        document.body.appendChild(heart);

        setTimeout(() => {
          heart.remove();
        }, 4000);
      }
    }
  </script>
</body>
</html>
