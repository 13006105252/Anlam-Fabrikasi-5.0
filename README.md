<!DOCTYPE html>
<html lang="tr">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Anlam Fabrikası</title>
  <style>
    body {
      margin: 0;
      padding: 20px;
      font-family: 'Segoe UI', sans-serif;
      background-color: #f2f2f2;
      color: #333;
    }
    .container {
      max-width: 480px;
      margin: auto;
      background: white;
      padding: 20px;
      border-radius: 16px;
      box-shadow: 0 4px 15px rgba(0,0,0,0.1);
    }
    h1 {
      font-size: 24px;
      color: #004080;
      text-align: center;
      margin-bottom: 16px;
    }
    textarea {
      width: 100%;
      height: 100px;
      font-size: 16px;
      padding: 10px;
      border-radius: 8px;
      border: 1px solid #ccc;
      box-sizing: border-box;
      resize: vertical;
    }
    button {
      display: block;
      width: 100%;
      padding: 14px;
      font-size: 16px;
      background-color: #004080;
      color: white;
      border: none;
      border-radius: 8px;
      margin-top: 12px;
      cursor: pointer;
      transition: background 0.3s;
    }
    button:hover {
      background-color: #00305a;
    }
    .ilham {
      background: #fff9db;
      padding: 10px;
      border-left: 5px solid #ffc107;
      border-radius: 6px;
      margin-bottom: 12px;
    }
    .ilham span {
      font-style: italic;
      color: #555;
    }
    #sonuc {
      margin-top: 20px;
      background: #f9f9f9;
      padding: 16px;
      border-radius: 12px;
      line-height: 1.6;
    }
    strong {
      color: #004080;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>🧠 Anlam Fabrikası</h1>

    <div class="ilham">
      <strong>💬 İlham Kutusu:</strong>
      <button onclick="ilhamVer()">🔁</button>
      <span id="ilhamCümlesi"></span>
    </div>

    <textarea id="girdi" placeholder="Duygunu yaz..."></textarea>
    <button onclick="anlamUret()">Anlam Üret</button>

    <div id="sonuc"></div>
  </div>

  <script>
    const ilhamlar = [
      "İçimde bir boşluk var, neyle dolacağını bilmiyorum.",
      "Kendimi bir yabancı gibi hissediyorum.",
      "Güçlü görünmeye çalışıyorum ama içim kırık.",
      "Kimse beni tam olarak anlamıyor.",
      "Sanki hayatımın anlamını kaybettim.",
      "Karanlıktan korkmuyorum, ama içimdeki sessizlikten ürküyorum.",
      "Biri gelip 'iyi misin?' dese, dağılacağım.",
      "Toparlanmak istiyorum ama nereden başlayacağımı bilmiyorum."
    ];

    const veriTabani = [
      {
        duygu: "Varoluşsal boşluk",
        temalar: ["sonsuzluk", "pus", "yankısızlık"],
        metafor: "Boş bir kutu",
        alinti: "Her şeyin anlamsız olduğu bir dünyada, insan anlamı kendisi yaratır.",
        yaratici: "Bir kutu gibi kalbim — içi dolu değil,<br>Boşluğu bile yankılanmıyor."
      },
      {
        duygu: "Kırılganlık",
        temalar: ["cam", "narinlik", "savunmasızlık"],
        metafor: "Çatlamış bir vazo",
        alinti: "Kırılmamak için kabuklanıyoruz, ama içimiz hâlâ cam gibi.",
        yaratici: "Beni tutan eller yok — sadece kırık parçalar<br>Çekilen her nefes, biraz daha dağılıyor içimden."
      },
      {
        duygu: "Yalnızlık",
        temalar: ["sessizlik", "uzaklık", "kopukluk"],
        metafor: "Issız bir ada",
        alinti: "Yalnızlık, bazen en derin denizlerin kıyısında sessizce bekleyen bir ada gibidir.",
        yaratici: "Issız bir ada gibi, çevremde ses yok,<br>Yalnızlığın rüzgarı esiyor, kalbimde fırtına."
      },
      {
        duygu: "Yalnızlık (Toparlanma)",
        temalar: ["umut", "yeniden doğuş", "destek"],
        metafor: "Doğuş yapan bir güneş",
        alinti: "Her geceyi takip eden bir gün doğar, umut ışığıyla dolar dünya.",
        yaratici: "Karanlık çekilip giderken ufuktan,<br>Doğar yeniden güneş, yüreğimde umut."
      }
    ];

    function ilhamVer() {
      const rastgele = ilhamlar[Math.floor(Math.random() * ilhamlar.length)];
      document.getElementById("ilhamCümlesi").textContent = `"${rastgele}"`;
      document.getElementById("girdi").value = rastgele;
    }

    function anlamUret() {
      const input = document.getElementById("girdi").value.trim();
      if (!input) {
        alert("Lütfen bir duygu yaz.");
        return;
      }

      const inputLower = input.toLowerCase();
      let secilen;

      if (
        inputLower.includes("topar") || 
        inputLower.includes("iyileş") || 
        inputLower.includes("daha iyi") || 
        inputLower.includes("yardım")
      ) {
        secilen = veriTabani.find(item => item.duygu === "Yalnızlık (Toparlanma)");
      } else {
        const filtrelenmis = veriTabani.filter(item => item.duygu !== "Yalnızlık (Toparlanma)");
        secilen = filtrelenmis[Math.floor(Math.random() * filtrelenmis.length)];
      }

      document.getElementById("sonuc").innerHTML = `
        🔍 <strong>Anlam Haritası</strong><br>
        <strong>Girdi:</strong> "${input}"<br>
        <strong>Duygu:</strong> ${secilen.duygu}<br>
        <strong>Temalar:</strong> ${secilen.temalar.join(", ")}<br>
        <strong>Metafor:</strong> ${secilen.metafor}<br>
        <strong>Alıntı:</strong> "${secilen.alinti}"<br><br>
        🎨 <strong>Yaratıcı Dönüşüm</strong><br>
        ${secilen.yaratici}
      `;
    }

    window.onload = ilhamVer;
  </script>
</body>
</html>
