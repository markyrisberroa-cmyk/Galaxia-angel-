<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<title>Ángel 💙</title>
<style>
body{
margin:0;
overflow:hidden;
background:black;
font-family:Arial, sans-serif;
}

canvas{
position:fixed;
top:0;
left:0;
z-index:0;
}

.center{
position:absolute;
top:50%;
left:50%;
transform:translate(-50%,-50%);
color:#00bfff;
font-size:60px;
font-weight:bold;
text-shadow:0 0 30px #00bfff, 0 0 60px #0088ff;
z-index:2;
}

.phrase{
position:absolute;
color:#66ccff;
font-size:12px;
white-space:nowrap;
opacity:0.8;
pointer-events:none;
}
</style>
</head>
<body>

<div class="center">Ángel</div>
<canvas id="stars"></canvas>

<script>
const canvas = document.getElementById("stars");
const ctx = canvas.getContext("2d");
canvas.width = window.innerWidth;
canvas.height = window.innerHeight;

// ⭐ Fondo galaxia
let stars = [];
for(let i=0;i<1000;i++){
stars.push({
x:Math.random()*canvas.width,
y:Math.random()*canvas.height,
size:Math.random()*1.5,
speed:Math.random()*0.3
});
}

function drawStars(){
ctx.clearRect(0,0,canvas.width,canvas.height);
ctx.fillStyle="white";
stars.forEach(star=>{
ctx.beginPath();
ctx.arc(star.x,star.y,star.size,0,Math.PI*2);
ctx.fill();

star.y+=star.speed;
if(star.y>canvas.height) star.y=0;
});
requestAnimationFrame(drawStars);
}
drawStars();

// 💙 Frases flotando alrededor
const frases = [
"Mi cochita","Mi papi","Mi bombón","Mi tesoro","Mi rey",
"Mi sol","Mi estrella","Mi universo","Mi cielo","Mi campeón",
"Mi vida","Mi orgullo","Mi hombre","Mi todo",
"Mi ángel hermoso","Mi fuerza","Mi príncipe","Mi corazón"
];

for(let i=0;i<150;i++){
let span = document.createElement("div");
span.className="phrase";
span.innerText = frases[Math.floor(Math.random()*frases.length)];

let angle = Math.random()*Math.PI*2;
let radius = 200 + Math.random()*250;

let x = canvas.width/2 + Math.cos(angle)*radius;
let y = canvas.height/2 + Math.sin(angle)*radius;

span.style.left = x+"px";
span.style.top = y+"px";

document.body.appendChild(span);
}
</script>

</body>
</html>