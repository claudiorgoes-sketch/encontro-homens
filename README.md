<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>Confirmação de Presença — 2º Encontro de Homens</title>
<style>
body{margin:0;font-family:Arial,sans-serif;background:#071018;color:#fff}
.wrap{max-width:720px;margin:auto;padding:20px}
.card{background:#101b24;border:2px solid #f4b51f;border-radius:18px;padding:24px;box-shadow:0 8px 30px #0008}
h1{color:#f4b51f;text-align:center;margin:0 0 8px}
h2{text-align:center;margin:0 0 22px}
.info{text-align:center;line-height:1.6;margin-bottom:22px}
label{display:block;font-weight:700;margin:16px 0 7px}
input,select,textarea{width:100%;box-sizing:border-box;padding:13px;border-radius:10px;border:1px solid #777;background:#fff;color:#111;font-size:16px}
button{width:100%;padding:15px;margin-top:22px;border:0;border-radius:12px;background:#f4b51f;color:#111;font-size:18px;font-weight:800;cursor:pointer}
small{color:#bbb}.hide{display:none}.success{padding:18px;background:#173c22;border-radius:12px;margin-top:20px}
</style>
</head>
<body>
<div class="wrap"><div class="card">
<h1>2º ENCONTRO DE HOMENS</h1>
<h2>“Haja e Reaja como um Sacerdote”</h2>
<div class="info">
📅 <b>14 de novembro de 2026</b><br>
🕓 <b>16:00 hs</b><br>
📍 <b>Rua Olívio Boa, 797 — Igreja Evangélica do Povo de Deus</b><br><br>
Confirme sua presença até <b>05/11/2026</b>.
</div>

<form id="form">
<label>Nome completo *</label><input name="nome" required>
<label>WhatsApp *</label><input name="whatsapp" inputmode="tel" required placeholder="(11) 99999-9999">
<label>Você confirma sua presença? *</label>
<select name="presenca" required><option value="">Selecione</option><option>Sim, estarei presente</option><option>Não poderei participar</option></select>
<label>Você irá acompanhado? *</label>
<select name="acompanhado" id="acompanhado" required><option value="">Selecione</option><option>Não, vou sozinho</option><option>Sim</option></select>
<div id="acompanhantes" class="hide">
<label>Quantidade de acompanhantes</label><input name="qtd" type="number" min="1" value="1">
<label>Nome dos acompanhantes</label><textarea name="nomes" rows="3"></textarea>
</div>
<label>Participará do churrasco/confraternização? *</label>
<select name="churrasco" required><option value="">Selecione</option><option>Sim</option><option>Não</option></select>
<label>Observações</label><textarea name="obs" rows="4" placeholder="Alguma informação que a organização precise saber?"></textarea>
<button type="submit">CONFIRMAR PRESENÇA</button>
</form>
<div id="msg" class="success hide"></div>
</div></div>

<script>
const acomp=document.getElementById('acompanhado');
const box=document.getElementById('acompanhantes');
acomp.addEventListener('change',()=>box.classList.toggle('hide',acomp.value!=='Sim'));

document.getElementById('form').addEventListener('submit',e=>{
 e.preventDefault();
 const f=new FormData(e.target), d=Object.fromEntries(f.entries());
 const text=`CONFIRMAÇÃO — 2º ENCONTRO DE HOMENS%0A%0ANome: ${encodeURIComponent(d.nome)}%0AWhatsApp: ${encodeURIComponent(d.whatsapp)}%0APresença: ${encodeURIComponent(d.presenca)}%0AAcompanhado: ${encodeURIComponent(d.acompanhado)}%0AQuantidade: ${encodeURIComponent(d.qtd||'0')}%0AAcompanhantes: ${encodeURIComponent(d.nomes||'')}%0AChurrasco: ${encodeURIComponent(d.churrasco)}%0AObservações: ${encodeURIComponent(d.obs||'')}`;
 const url='https://wa.me/5511973850139?text='+text;
 document.getElementById('msg').classList.remove('hide');
 document.getElementById('msg').innerHTML='✅ <b>Formulário preenchido!</b><br>Clique no botão abaixo para enviar sua confirmação à organização.<br><br><a href="'+url+'" target="_blank" style="color:#f4b51f;font-weight:bold">ENVIAR CONFIRMAÇÃO PELO WHATSAPP</a>';
});
</script>
</body>
</html>
