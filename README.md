# -öylelimsi
# Kullanıcının onayıyla dosya tekrar oluşturuluyor

# index.html
index_html = """<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <title>Melek'e Özel</title>
    <link rel="stylesheet" href="stil.css">
</head>
<body class="bg">
    <div class="kalpler">
        <div class="kalp">❤️</div><div class="kalp">💖</div><div class="kalp">💕</div><div class="kalp">💘</div>
    </div>
    <div class="container">
        <h1>Merhaba Melek 🌸</h1>
        <p>Bu site senin için... Çünkü sen özelsin 💖</p>
        <img src="resimler/melek.jpg" alt="Melek" class="image">
        <div class="butonlar">
            <a href="sozler.html" class="buton">❤️ Güzel Sözler</a>
            <a href="muzik.html" class="buton">Senin İçin Bir Müzik</a>
        </div>
        <footer>Hazırlayan: Sana değer veren İhsan</footer>
    </div>
</body>
</html>"""

# sozler.html
sozler_html = """<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <title>Melek'e Sözler</title>
    <link rel="stylesheet" href="stil.css">
    <script>
        const sozler = [
            "Sen gülünce dünya susuyor, kalbim konuşuyor.",
            "Sen benim en güzel tesadüfümsün Melek.",
            "Gözlerinde kaybolmak bile huzur veriyor.",
            "Her bakışın bir şiir, her gülüşün bir melodidir.",
            "Sen hayatıma düşen en güzel cümlesin.",
            "Kalbimin en güzel köşesi sana ait.",
            "Varlığın hayatımın şiiri oldu.",
            "Sana bakmak bir ömre bedel."
        ];
        function yeniSoz() {
            const rastgele = Math.floor(Math.random() * sozler.length);
            document.getElementById("soz").innerText = sozler[rastgele];
        }
        window.onload = yeniSoz;
    </script>
</head>
<body class="bg">
    <div class="kalpler">
        <div class="kalp">❤️</div><div class="kalp">💖</div><div class="kalp">💕</div><div class="kalp">💘</div>
    </div>
    <div class="container">
        <h1>Senin İçin Sözler 💌</h1>
        <p id="soz"></p>
        <button class="buton" onclick="yeniSoz()">Yenile 🔁</button>
        <a href="index.html" class="buton">Ana Sayfa</a>
    </div>
</body>
</html>"""

# muzik.html
muzik_html = """<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <title>Melek'e Müzik</title>
    <link rel="stylesheet" href="stil.css">
</head>
<body class="bg">
    <div class="kalpler">
        <div class="kalp">❤️</div><div class="kalp">💖</div><div class="kalp">💕</div><div class="kalp">💘</div>
    </div>
    <div class="container">
        <h1>Senin İçin Seçtiğim Bir Melodi 🎶</h1>
        <p>"Love Song" - Adele</p>
        <audio controls autoplay>
            <source src="muzik/lovesong.mp3" type="audio/mpeg">
            Tarayıcınız müzik çalmayı desteklemiyor.
        </audio>
        <div class="galeri">
            <img src="resimler/melek.jpg" alt="Melek Fotoğraf 1">
            <img src="resimler/melek2.jpg" alt="Melek Fotoğraf 2">
        </div>
        <a href="index.html" class="buton">Ana Sayfa</a>
    </div>
</body>
</html>"""

# stil.css
stil_css = """body {
    font-family: 'Segoe UI', sans-serif;
    text-align: center;
    padding: 30px;
    margin: 0;
    color: #4b004f;
}

.bg {
    background: url('resimler/gul-arkaplan.jpg') no-repeat center center fixed;
    background-size: cover;
    position: relative;
    overflow: hidden;
}

.container {
    max-width: 700px;
    margin: auto;
    padding: 20px;
    border-radius: 15px;
    background: rgba(255, 255, 255, 0.9);
    box-shadow: 0 0 10px rgba(0,0,0,0.1);
    position: relative;
    z-index: 1;
}

.image {
    width: 200px;
    border-radius: 50%;
    margin: 20px 0;
}

.galeri img {
    width: 200px;
    margin: 10px;
    border-radius: 10px;
    box-shadow: 0 0 5px rgba(0,0,0,0.3);
}

.butonlar {
    margin-top: 20px;
}

.buton {
    text-decoration: none;
    padding: 10px 20px;
    background-color: #e75480;
    color: white;
    border-radius: 10px;
    margin: 10px;
    display: inline-block;
    font-size: 16px;
    cursor: pointer;
}

.buton:hover {
    background-color: #d63a6c;
}

footer {
    margin-top: 30px;
    font-style: italic;
}

.kalpler {
    position: absolute;
    width: 100%;
    height: 100%;
    overflow: hidden;
    z-index: 0;
}

.kalp {
    position: absolute;
    animation: ucus 10s infinite ease-in-out;
    font-size: 30px;
    top: 100%;
    left: 50%;
    transform: translateX(-50%);
    opacity: 0;
}

@keyframes ucus {
    0% { top: 100%; opacity: 0; }
    50% { opacity: 1; }
    100% { top: -10%; opacity: 0; transform: translateX(-50%) rotate(360deg); }
}"""

# Dosya oluşturma işlemi
import os
from zipfile import ZipFile

base_path = "/mnt/data/melek-sitesi"
os.makedirs(f"{base_path}/resimler", exist_ok=True)
os.makedirs(f"{base_path}/muzik", exist_ok=True)

with open(f"{base_path}/index.html", "w", encoding="utf-8") as f:
    f.write(index_html)

with open(f"{base_path}/sozler.html", "w", encoding="utf-8") as f:
    f.write(sozler_html)

with open(f"{base_path}/muzik.html", "w", encoding="utf-8") as f:
    f.write(muzik_html)

with open(f"{base_path}/stil.css", "w", encoding="utf-8") as f:
    f.write(stil_css)

# Yer tutucu dosyalar
for filename in ["melek.jpg", "melek2.jpg", "gul-arkaplan.jpg"]:
    with open(f"{base_path}/resimler/{filename}", "wb") as f:
        f.write(b"")

with open(f"{base_path}/muzik/lovesong.mp3", "wb") as f:
    f.write(b"")

# ZIP oluşturma
zip_path = "/mnt/data/melek-sitesi.zip"
with ZipFile(zip_path, "w") as zipf:
    for foldername, subfolders, filenames in os.walk(base_path):
        for filename in filenames:
            filepath = os.path.join(foldername, filename)
            arcname = os.path.relpath(filepath, base_path)
            zipf.write(filepath, arcname)

zip_path
