<!DOCTYPE html>
<html lang="pt-BR"><head><meta charset="UTF-8"><meta name="viewport" content="width=device-width,initial-scale=1">
<title>Confirmação de Presença — 2º Encontro de Homens</title>
<style>
body{margin:0;font-family:Arial,sans-serif;background:#071018;color:#fff}.wrap{max-width:720px;margin:auto;padding:20px}
.card{background:#101b24;border:2px solid #f4b51f;border-radius:18px;padding:24px;box-shadow:0 8px 30px #0008}
h1{color:#f4b51f;text-align:center;margin:0 0 8px}h2{text-align:center;margin:0 0 22px}.info{text-align:center;line-height:1.6;margin-bottom:22px}
label{display:block;font-weight:700;margin:16px 0 7px}input,select,textarea{width:100%;box-sizing:border-box;padding:13px;border-radius:10px;border:1px solid #777;background:#fff;color:#111;font-size:16px}
button{width:100%;padding:15px;margin-top:22px;border:0;border-radius:12px;background:#f4b51f;color:#111;font-size:18px;font-weight:800;cursor:pointer}button:disabled{opacity:.6}.hide{display:none}
.success{padding:18px;background:#173c22;border-radius:12px;margin-top:20px}.error{padding:18px;background:#542020;border-radius:12px;margin-top:20px}a{color:#f4b51f;font-weight:bold}
</style></head><body><div class="wrap"><div class="card">
<h1>2º ENCONTRO DE HOMENS</h1><h2>“AJA E REAJA COMO UM SACERDOTE”</h2>
<div class="info">📅 <b>14 de novembro de 2026</b><br>🕓 <b>16:00 hs</b><br>📍 <b>Rua Olívio Boa, 797 — Igreja Evangélica do Povo de Deus</b><br><br>Confirme sua presença até <b>05/11/2026</b>.</div>
<form id="form">
<label>Nome completo *</label><input name="nome" required>
<label>WhatsApp *</label><input name="whatsapp" inputmode="tel" required placeholder="(11) 99999-9999">
<label>Você confirma sua presença? *</label><select name="presenca" required><option value="">Selecione</option><option>Sim, estarei presente</option><option>Não poderei participar</option></select>
<label>Você irá acompanhado? *</label><select name="acompanhado" id="acompanhado" required><option value="">Selecione</option><option>Não, vou sozinho</option><option>Sim</option></select>
<div id="acompanhantes" class="hide"><label>Quantidade de acompanhantes</label><input name="qtd" type="number" min="1" value="1"><label>Nome dos acompanhantes</label><textarea name="nomes" rows="3"></textarea></div>
<label>Participará do churrasco/confraternização? *</label><select name="churrasco" required><option value="">Selecione</option><option>Sim</option><option>Não</option></select>
<label>Observações</label><textarea name="obs" rows="4"></textarea>
<button id="btn" type="submit">CONFIRMAR PRESENÇA</button></form><div id="msg" class="hide"></div>
</div></div>
<script>
const ENDPOINT = "https://script.google.com/macros/s/AKfycbyRSAomqrAsU5aHGYAcINjUmmrUt1KHU66HIywF0Jld7dR0pWNurhXWkAZc-lnTZhUfMA/exec";
const WHATSAPP = "5511973850139";
const form=document.getElementById("form"), acomp=document.getElementById("acompanhado"), box=document.getElementById("acompanhantes"), btn=document.getElementById("btn"), msg=document.getElementById("msg");
acomp.addEventListener("change",()=>box.classList.toggle("hide",acomp.value!=="Sim"));
form.addEventListener("submit",async e=>{
 e.preventDefault(); btn.disabled=true; btn.textContent="REGISTRANDO...";
 const d=Object.fromEntries(new FormData(form).entries());
 const params=new URLSearchParams({nome:d.nome||"",whatsapp:d.whatsapp||"",presenca:d.presenca||"",acompanhado:d.acompanhado||"",qtd:d.qtd||"0",nomes:d.nomes||"",churrasco:d.churrasco||"",obs:d.obs||""});
 try{
   await fetch(ENDPOINT+"?"+params.toString(),{method:"GET",mode:"no-cors"});
   const text="CONFIRMAÇÃO — 2º ENCONTRO DE HOMENS\n\nNome: "+d.nome+"\nWhatsApp: "+d.whatsapp+"\nPresença: "+d.presenca+"\nAcompanhado: "+d.acompanhado+"\nQuantidade: "+(d.qtd||"0")+"\nAcompanhantes: "+(d.nomes||"")+"\nChurrasco: "+d.churrasco+"\nObservações: "+(d.obs||"");
   const wa="https://wa.me/"+WHATSAPP+"?text="+encodeURIComponent(text);
   msg.className="success"; msg.innerHTML="✅ <b>Presença registrada!</b><br><br>Sua confirmação foi enviada para a lista de participantes.<br><br><a href='"+wa+"' target='_blank'>📲 ENVIAR TAMBÉM PELO WHATSAPP</a>";
   form.reset(); box.classList.add("hide");
 }catch(err){msg.className="error";msg.innerHTML="⚠️ Não foi possível registrar a confirmação. Tente novamente."}
 btn.disabled=false;btn.textContent="CONFIRMAR PRESENÇA";
});
</script></body></html>
