<!DOCTYPE html>
<html>
<head>

<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Will You Be My Valentine ❤️</title>

<style>

body{
  margin:0;
  padding:0;
  text-align:center;
  font-family:Arial, sans-serif;
  background:linear-gradient(135deg,#ff9a9e,#fecfef);
  overflow:hidden;
}

.container{
  margin-top:40px;
  padding:20px;
}

h1{
  color:white;
  font-size:28px;
}

p{
  color:white;
  font-size:18px;
}

button{
  padding:15px 25px;
  font-size:18px;
  margin:15px;
  border:none;
  border-radius:12px;
  cursor:pointer;
}

#yes{
  background:#ff4d6d;
  color:white;
}

#no{
  background:#333;
  color:white;
  position:absolute;
}

.gif{
  width:80%;
  max-width:260px;
  border-radius:20px;
  margin-top:15px;
}

</style>
</head>

<body>

<div class="container">

<h1 id="question">Shizu💗 Will You Be My Valentine? ❤️</h1>

<p>I have something special to ask you Shizu 🥺</p>

<!-- Working Giphy GIFs -->
<img class="gif"
src="https://media.giphy.com/media/l0MYt5jPR6QX5pnqM/giphy.gif">

<br>

<button id="yes" onclick="yesClick()">YES 💖</button>
<button id="no" ontouchstart="moveNo()" onmouseover="moveNo()">NO 😢</button>

</div>

<script>

let texts = [
"Think again please 🥺",
"Are you sure? 💔",
"Please don’t break my heart 😭",
"I’ll give you chocolates 🍫",
"I’ll keep you happy forever ❤️",
"Last chance… say YES 😌",
"You can’t escape love 😏",
"Think again cutie 🥰"
];

let i = 0;

function moveNo(){

  let width = window.innerWidth - 120;
  let height = window.innerHeight - 120;

  let x = Math.random() * width;
  let y = Math.random() * height;

  let btn = document.getElementById("no");
  btn.style.left = x + "px";
  btn.style.top = y + "px";

  document.getElementById("question").innerText = texts[i];

  i++;
  if(i >= texts.length){ i = 0; }
}

function yesClick(){

document.body.innerHTML = `

<style>

body{
  margin:0;
  overflow:hidden;
  background:linear-gradient(135deg,#ff758c,#ffb6c1);
  font-family:Arial, sans-serif;
  text-align:center;
  color:white;
}

/* Text layer */
.content{
  position:relative;
  z-index:2;
  margin-top:60px;
}

/* Hearts rain */
.heart{
  position:fixed;
  top:-10px;
  font-size:24px;
  animation:fall linear infinite;
  z-index:2;
}

@keyframes fall{
  to{
    transform:translateY(110vh);
  }
}

/* Fireworks canvas */
canvas{
  position:fixed;
  top:0;
  left:0;
  z-index:1;
}

</style>

<div class="content">

<h1 style="font-size:32px;">
Yayyyyy ❤️ She Said YES 😍
</h1>

<p style="font-size:20px;">
I Love You Shizu 💖<br>
Happy Valentine’s Day 🌹
</p>

<img style="width:80%;max-width:260px;border-radius:20px;"
src="https://media.giphy.com/media/MDJ9IbxxvDUQM/giphy.gif">

<h2>Forever Together 💑</h2>

</div>

<canvas id="fireworks"></canvas>

<!-- Romantic Music -->
<audio autoplay loop>
<source src="https://www2.cs.uic.edu/~i101/SoundFiles/Perfect.mp3" type="audio/mpeg">
</audio>

`;

/* ❤️ Hearts Rain */
for(let i=0;i<40;i++){
  let heart=document.createElement("div");
  heart.className="heart";
  heart.innerHTML="❤️";
  heart.style.left=Math.random()*100+"vw";
  heart.style.animationDuration=(3+Math.random()*5)+"s";
  document.body.appendChild(heart);
}

/* 🎆 Colourful Fireworks */

let canvas=document.getElementById("fireworks");
let ctx=canvas.getContext("2d");

canvas.width=window.innerWidth;
canvas.height=window.innerHeight;

let particles=[];

function randomColor(){
  const colors=["#ff4d6d","#ffd60a","#00f5d4","#9b5de5","#f15bb5","#00bbf9"];
  return colors[Math.floor(Math.random()*colors.length)];
}

function createFirework(){

  let x=Math.random()*canvas.width;
  let y=Math.random()*canvas.height/2;
  let color=randomColor();

  for(let i=0;i<70;i++){
    particles.push({
      x:x,
      y:y,
      dx:(Math.random()-0.5)*7,
      dy:(Math.random()-0.5)*7,
      life:100,
      color:color
    });
  }
}

function animate(){

  ctx.fillStyle="rgba(0,0,0,0.15)";
  ctx.fillRect(0,0,canvas.width,canvas.height);

  particles.forEach((p,index)=>{
    p.x+=p.dx;
    p.y+=p.dy;
    p.life--;

    ctx.beginPath();
    ctx.arc(p.x,p.y,3,0,Math.PI*2);
    ctx.fillStyle=p.color;
    ctx.fill();

    if(p.life<=0){
      particles.splice(index,1);
    }
  });

  requestAnimationFrame(animate);
}

setInterval(createFirework,800);
animate();

}

</script>

</body>
</html>
