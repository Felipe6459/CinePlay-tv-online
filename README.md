<!DOCTYPE html>
<html lang="pt-br">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Cineplay TV</title>

<style>
*{margin:0;padding:0;box-sizing:border-box}
html,body{
overflow-x:hidden;
font-family:Arial;
color:#fff;
text-align:center;
}

body{
background: linear-gradient(180deg,#0b0b0b,#1a0033);
}

/* fundo animado corrigido */
body::before{
content:"";
position:fixed;
top:0;
left:0;
width:120%;
height:120%;
background: radial-gradient(circle at 20% 30%, rgba(123,44,255,0.3), transparent),
            radial-gradient(circle at 80% 70%, rgba(255,0,100,0.3), transparent);
z-index:-1;
animation: moverBg 10s infinite alternate;
}

@keyframes moverBg{
0%{transform:translate(0,0)}
100%{transform:translate(-30px, -30px)}
}

/* header */
.header{
background: linear-gradient(90deg,#7b2cff,#ff0066);
padding:12px;
font-weight:bold;
}

/* banner */
.banner{
padding:70px 20px;
}

.overlay{
background:rgba(0,0,0,0.7);
padding:30px;
border-radius:10px;
}

/* botão */
.btn{
display:block;
margin:12px auto;
padding:15px;
background: linear-gradient(45deg,#ff2d2d,#ff0066);
color:#fff;
text-decoration:none;
border-radius:12px;
width:90%;
max-width:320px;
font-weight:bold;
animation:pulsar 1.5s infinite;
box-shadow:0 0 15px rgba(255,0,100,0.5);
position:relative;
overflow:hidden;
}

.btn::after{
content:"";
position:absolute;
top:0;
left:-100%;
width:100%;
height:100%;
background: linear-gradient(120deg,transparent,rgba(255,255,255,0.4),transparent);
}

.btn:hover::after{
left:100%;
transition:0.5s;
}

/* cards */
.card{
background: linear-gradient(145deg,#1a1a1a,#0d0d0d);
margin:15px auto;
padding:20px;
border-radius:20px;
max-width:350px;
box-shadow:0 0 20px rgba(0,0,0,0.5);
transition:0.3s;
}

.card:hover{
transform:scale(1.05);
}

.highlight{border:2px solid #7b2cff}
.price{font-size:22px;color:#7b2cff;margin:10px 0}

/* animações */
@keyframes pulsar{
0%{transform:scale(1)}
50%{transform:scale(1.05)}
100%{transform:scale(1)}
}

@keyframes flutuar{
0%{transform:translateY(0)}
50%{transform:translateY(-10px)}
100%{transform:translateY(0)}
}

@keyframes brilho{
0%{opacity:0.6}
50%{opacity:1}
100%{opacity:0.6}
}

.fade-in{
opacity:0;
transform:translateY(20px);
animation:fadeIn 1s forwards;
}

@keyframes fadeIn{
to{opacity:1;transform:translateY(0)}
}

/* extras */
.popup{
position:fixed;
bottom:10px;
left:10px;
background:#111;
padding:10px 15px;
border-radius:10px;
font-size:13px;
display:none;
}

.whatsapp-float{
position:fixed;
bottom:20px;
right:20px;
background:#25D366;
color:#fff;
padding:15px;
border-radius:50%;
text-decoration:none;
font-size:22px;
}
</style>
</head>

<body>

<div class="header">
🔥 OFERTA LIMITADA TERMINA EM <span id="timer"></span>
<p style="color:red;">⚠️ Restam poucas vagas hoje</p>
</div>

<div class="banner fade-in">
<div class="overlay">

<h1 style="font-size:32px;">🎬 Cineplay TV</h1>

<h2 style="color:#ff4444;">
🔥 Cancele Netflix, Prime e outros e pague muito mais barato
</h2>

<p>
🎬 +100 MIL conteúdos liberados<br>
📺 Canais ao vivo + Premiere + Telecine<br>
⚡ Sem travar | HD/FULL HD
</p>

<a class="btn" href="https://wa.me/5582996062108?text=Quero%20teste%20gratis%20agora">
🔥 TESTE GRÁTIS AGORA
</a>

<p style="color:#00ff88;font-weight:bold;">
🚀 Acesso liberado em poucos minutos
</p>

<p style="color:#00ff88;">
👥 <span id="online"></span> pessoas vendo agora
</p>

<div style="margin-top:30px;">
<div style="display:inline-block;background:#111;padding:10px;border-radius:30px;box-shadow:0 0 20px rgba(0,0,0,0.5);animation: flutuar 3s infinite;">
<img src="https://i.postimg.cc/SsXBVsR2/Screenshot-20260406-193310-IBO-REVENDA.jpg"
style="width:220px;border-radius:20px;animation: brilho 2s infinite;box-shadow:0 0 25px rgba(0,0,0,0.7);max-width:100%;">
</div>
</div>

</div>
</div>

<div class="container fade-in">

<h2>💰 Pagamento via Pix</h2>

<div style="background:#111;padding:15px;border-radius:10px;margin:15px;">
<p><b>3c3a8735-4475-4340-8090-649f95432cfa</b></p>

<button class="btn" onclick="copiarPix()">📋 Copiar chave Pix</button>

<a class="btn" href="https://wa.me/5582996062108?text=Já%20fiz%20o%20pagamento">
📲 Enviar comprovante
</a>
</div>

<h2>💰 Planos Mensais</h2>

<div class="card">
<h3>1 Tela</h3>
<div class="price">R$ 24,90</div>
<a class="btn" href="#">Assinar</a>
</div>

<div class="card highlight">
<h3>2 Telas ⭐ Mais Vendido</h3>
<div class="price">R$ 34,90</div>
<a class="btn" href="#">Assinar</a>
</div>

<div class="card">
<h3>3 Telas</h3>
<div class="price">R$ 39,90</div>
<a class="btn" href="#">Assinar</a>
</div>

</div>

<a class="whatsapp-float" href="https://wa.me/5582996062108">💬</a>

<div class="popup" id="popup"></div>

<script>
function copiarPix(){
navigator.clipboard.writeText("3c3a8735-4475-4340-8090-649f95432cfa");
alert("Chave Pix copiada!");
}

/* TIMER */
let time = 600;
const timerInterval = setInterval(()=>{
let m = Math.floor(time/60);
let s = time%60;
document.getElementById('timer').innerHTML = m+":"+(s<10?'0':'')+s;

if(time <= 0){
clearInterval(timerInterval);
} else {
time--;
}
},1000);

/* CONTADOR SUAVE */
let pessoas = 12;

setInterval(()=>{
let variacao = Math.floor(Math.random()*3) - 1;
pessoas += variacao;

if(pessoas < 8) pessoas = 8;
if(pessoas > 25) pessoas = 25;

document.getElementById("online").innerHTML = pessoas;
},3000);

/* POPUP */
const nomes=["João - SP","Maria - RJ","Carlos - MG","Ana - BA","Tiago - Lisboa","Sofia - Porto"];

setInterval(()=>{
let popup=document.getElementById("popup");
let nome=nomes[Math.floor(Math.random()*nomes.length)];
popup.innerHTML="💰 "+nome+" acabou de assinar!";
popup.style.display="block";

setTimeout(()=>{
popup.style.display="none";
},3000);

},8000);
</script>

</body>
</html>
