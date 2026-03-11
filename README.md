# CortesVirais
Ferramenta web para gerar cortes de vídeo automaticamente para TikTok,Kwai,Shorts 
<!DOCTYPE html>
<html lang="pt-br">

<head>
<meta charset="UTF-8">
<title>ClipForge AI</title>

<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;500;700&display=swap" rel="stylesheet">

<style>

*{
margin:0;
padding:0;
box-sizing:border-box;
}

body{
font-family:'Poppins',sans-serif;
background:linear-gradient(135deg,#020617,#0f172a);
color:white;
text-align:center;
min-height:100vh;
}

header{
padding:40px;
font-size:32px;
font-weight:700;
color:#22c55e;
}

.sub{
opacity:.7;
margin-bottom:40px;
}

.container{
max-width:900px;
margin:auto;
padding:20px;
}

.upload-area{

border:2px dashed #22c55e;
border-radius:15px;
padding:50px;
cursor:pointer;
transition:.3s;
}

.upload-area:hover{
background:#020617;
}

button{

margin-top:20px;
padding:15px 30px;
border:none;
border-radius:10px;
background:#22c55e;
font-size:16px;
cursor:pointer;
font-weight:600;

}

button:hover{
background:#16a34a;
}

video{
margin-top:25px;
width:100%;
border-radius:10px;
}

.progress{

margin-top:30px;
height:18px;
background:#1e293b;
border-radius:20px;
overflow:hidden;

}

.bar{

height:100%;
width:0%;
background:linear-gradient(90deg,#22c55e,#4ade80);

}

.clips{

margin-top:40px;
display:grid;
grid-template-columns:repeat(auto-fit,minmax(200px,1fr));
gap:20px;

}

.clip{

background:#020617;
padding:20px;
border-radius:12px;
border:1px solid #22c55e;

}

footer{

margin-top:60px;
opacity:.5;
font-size:14px;

}

</style>

</head>

<body>

<header>CortesVirais AI</header>

<div class="sub">
Transforme vídeos longos em cortes para TikTok, Reels e Shorts
</div>

<div class="container">

<div class="upload-area" id="dropArea">

Arraste seu vídeo aqui ou clique para enviar

<input type="file" id="videoInput" hidden>

</div>

<button onclick="processar()">Gerar Cortes</button>

<video id="preview" controls style="display:none;"></video>

<div class="progress">
<div class="bar" id="bar"></div>
</div>

<div class="clips" id="resultado"></div>

</div>

<footer>
CortesVirais AI © 2026
</footer>

<script>

let dropArea=document.getElementById("dropArea")
let input=document.getElementById("videoInput")

dropArea.addEventListener("click",()=>input.click())

dropArea.addEventListener("dragover",(e)=>{
e.preventDefault()
dropArea.style.borderColor="#4ade80"
})

dropArea.addEventListener("dragleave",()=>{
dropArea.style.borderColor="#22c55e"
})

dropArea.addEventListener("drop",(e)=>{
e.preventDefault()
input.files=e.dataTransfer.files
mostrarVideo()
})

input.addEventListener("change",mostrarVideo)

function mostrarVideo(){

let file=input.files[0]

if(!file)return

let video=document.getElementById("preview")

video.src=URL.createObjectURL(file)

video.style.display="block"

}

function processar(){

let bar=document.getElementById("bar")

let width=0

let intervalo=setInterval(()=>{

if(width>=100){

clearInterval(intervalo)

mostrarClips()

}else{

width++

bar.style.width=width+"%"

}

},30)

}

function mostrarClips(){

let resultado=document.getElementById("resultado")

resultado.innerHTML=`

<div class="clip">

🎬 Clip 1<br>
Duração: 30s<br><br>

<button>Baixar</button>

</div>

<div class="clip">

🔥 Clip 2<br>
Duração: 1:00m<br><br>

<button>Baixar</button>

</div>

<div class="clip">

🚀 Clip 3<br>
Duração: 1:30s<br><br>

<button>Baixar</button>

</div>

<div class="clip">

⭐ Clip 4<br>
Duração: 2:00m<br><br>

<button>Baixar</button>

</div>

`

}

</script>

</body>
</html>