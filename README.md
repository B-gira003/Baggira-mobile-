<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Baggira Mobile</title>

<style>
* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
    font-family: Arial, sans-serif;
}

body {
    background: #f4f7f6;
    color: #17211f;
}

.app {
    max-width: 430px;
    margin: auto;
    min-height: 100vh;
    background: white;
    padding-bottom: 80px;
}

header {
    background: #087f5b;
    color: white;
    padding: 25px 20px;
    border-radius: 0 0 25px 25px;
}

.logo {
    font-size: 25px;
    font-weight: bold;
}

.welcome {
    margin-top: 20px;
    font-size: 15px;
}

.balance {
    margin-top: 8px;
    font-size: 30px;
    font-weight: bold;
}

.card {
    margin: 20px;
    padding: 20px;
    border-radius: 20px;
    background: #ffffff;
    box-shadow: 0 5px 20px rgba(0,0,0,0.08);
}

.actions {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 12px;
}

.action {
    border: none;
    background: #f0f8f5;
    padding: 18px 10px;
    border-radius: 15px;
    font-size: 15px;
    cursor: pointer;
}

.action span {
    display: block;
    font-size: 25px;
    margin-bottom: 7px;
}

h2 {
    margin-bottom: 15px;
    font-size: 20px;
}

.transaction {
    display: flex;
    justify-content: space-between;
    padding: 14px 0;
    border-bottom: 1px solid #eee;
}

.green {
    color: #087f5b;
}

.red {
    color: #d94841;
}

.page {
    display: none;
    padding-bottom: 20px;
}

.page.active {
    display: block;
}

.message {
    padding: 15px;
    margin-bottom: 10px;
    background: #f4f7f6;
    border-radius: 15px;
}

input {
    width: 100%;
    padding: 14px;
    margin: 8px 0;
    border: 1px solid #ddd;
    border-radius: 12px;
    font-size: 16px;
}

button.primary {
    width: 100%;
    padding: 15px;
    background: #087f5b;
    color: white;
    border: none;
    border-radius: 12px;
    font-size: 16px;
    margin-top: 10px;
}

nav {
    position: fixed;
    bottom: 0;
    left: 50%;
    transform: translateX(-50%);
    width: 100%;
    max-width: 430px;
    background: white;
    display: flex;
    justify-content: space-around;
    padding: 12px 5px;
    box-shadow: 0 -3px 15px rgba(0,0,0,0.1);
}

nav button {
    background: none;
    border: none;
    font-size: 12px;
    color: #555;
}

nav span {
    display: block;
    font-size: 22px;
    margin-bottom: 3px;
}
</style>
</head>

<body>

<div class="app">

<header>
    <div class="logo">Baggira Mobile</div>
    <div class="welcome">Bienvenue 👋</div>
    <div class="balance" id="balance">250 000 CDF</div>
</header>

<!-- ACCUEIL -->
<section id="home" class="page active">

<div class="card">
<h2>Actions rapides</h2>

<div class="actions">

<button class="action" onclick="showPage('send')">
<span>💸</span>
Envoyer
</button>

<button class="action" onclick="showPage('receive')">
<span>📥</span>
Recevoir
</button>

<button class="action" onclick="showPage('messages')">
<span>💬</span>
Messages
</button>

<button class="action" onclick="showPage('wallet')">
<span>💰</span>
Portefeuille
</button>

</div>
</div>

<div class="card">
<h2>Dernières transactions</h2>

<div class="transaction">
<span>Jean</span>
<span class="red">- 20 000 CDF</span>
</div>

<div class="transaction">
<span>Marie</span>
<span class="green">+ 50 000 CDF</span>
</div>

<div class="transaction">
<span>Paiement service</span>
<span class="red">- 5 000 CDF</span>
</div>

</div>

</section>

<!-- PORTEFEUILLE -->
<section id="wallet" class="page">

<div class="card">
<h2>💰 Mon portefeuille</h2>

<p>Solde disponible</p>
<h1 style="margin:10px 0 20px;">250 000 CDF</h1>

<div class="transaction">
<span>Entrée d'argent</span>
<span class="green">+50 000</span>
</div>

<div class="transaction">
<span>Transfert</span>
<span class="red">-20 000</span>
</div>

<div class="transaction">
<span>Service</span>
<span class="red">-5 000</span>
</div>

</div>

</section>

<!-- MESSAGES -->
<section id="messages" class="page">

<div class="card">
<h2>💬 Messages</h2>

<div class="message">
<strong>Jean</strong><br>
Salut, comment vas-tu ?
</div>

<div class="message">
<strong>Marie</strong><br>
Merci pour le transfert 👍
</div>

<div class="message">
<strong>Patrick</strong><br>
Tu es disponible aujourd'hui ?
</div>

<input id="messageInput" placeholder="Écrire un message...">

<button class="primary" onclick="sendMessage()">
Envoyer
</button>

</div>

</section>

<!-- ENVOYER -->
<section id="send" class="page">

<div class="card">
<h2>💸 Envoyer de l'argent</h2>

<input id="receiver" placeholder="Numéro du destinataire">

<input id="amount" type="number" placeholder="Montant en CDF">

<button class="primary" onclick="sendMoney()">
Confirmer le transfert
</button>

<p id="sendResult" style="margin-top:15px;"></p>

</div>

</section>

<!-- RECEVOIR -->
<section id="receive" class="page">

<div class="card">
<h2>📥 Recevoir de l'argent</h2>

<p>Votre numéro Baggira Mobile :</p>

<h2 style="margin-top:15px;">+243 XXX XXX XXX</h2>

<p style="margin-top:15px;">
Partagez ce numéro pour recevoir de l'argent.
</p>

</div>

</section>

<!-- PROFIL -->
<section id="profile" class="page">

<div class="card">
<h2>👤 Mon profil</h2>

<p><strong>Nom :</strong> Justin</p>
<p style="margin-top:10px;"><strong>Service :</strong> Baggira Mobile</p>
<p style="margin-top:10px;"><strong>Statut :</strong> Compte démo</p>

<button class="primary">
Modifier mon profil
</button>

</div>

</section>

<!-- NAVIGATION -->
<nav>

<button onclick="showPage('home')">
<span>🏠</span>
Accueil
</button>

<button onclick="showPage('messages')">
<span>💬</span>
Messages
</button>

<button onclick="showPage('wallet')">
<span>💰</span>
Portefeuille
</button>

<button onclick="showPage('profile')">
<span>👤</span>
Profil
</button>

</nav>

</div>

<script>

function showPage(pageId) {

    document.querySelectorAll('.page').forEach(page => {
        page.classList.remove('active');
    });

    document.getElementById(pageId).classList.add('active');

    window.scrollTo(0, 0);
}

function sendMessage() {

    const input = document.getElementById("messageInput");

    if(input.value.trim() === "") {
        alert("Écrivez un message.");
        return;
    }

    alert("Message envoyé !");
    input.value = "";
}

function sendMoney() {

    const receiver = document.getElementById("receiver").value;
    const amount = Number(document.getElementById("amount").value);
    const result = document.getElementById("sendResult");

    if(receiver === "" || amount <= 0) {
        result.innerHTML = "⚠️ Veuillez remplir tous les champs.";
        result.style.color = "red";
        return;
    }

    result.innerHTML =
        "✅ Transfert simulé de " +
        amount.toLocaleString() +
        " CDF vers " +
        receiver;

    result.style.color = "#087f5b";
}

</script>

</body>
</html> 
