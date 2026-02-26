<!DOCTYPE html>
<html lang="pt">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>KUVUNA - Plataforma</title>
<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

<style>
body { margin:0; font-family: Arial, sans-serif; background:#f4f6f9; }
header {
    background:#0E7C4F;
    color:#fff;
    padding:15px 20px;
    display:flex;
    justify-content:space-between;
    align-items:center;
}
nav {
    width:220px;
    background:#111;
    height:100vh;
    position:fixed;
    top:0;
    left:0;
    padding-top:70px;
}
nav button {
    width:100%;
    padding:15px;
    border:none;
    background:none;
    color:#fff;
    text-align:left;
    cursor:pointer;
}
nav button:hover { background:#0E7C4F; }

main {
    margin-left:220px;
    padding:30px;
}

.card {
    background:#fff;
    padding:20px;
    margin-bottom:20px;
    border-radius:8px;
    box-shadow:0 2px 6px rgba(0,0,0,0.1);
}

.hidden { display:none; }

.btn {
    background:#0E7C4F;
    color:#fff;
    border:none;
    padding:10px 15px;
    border-radius:5px;
    cursor:pointer;
}
.btn:hover { background:#0b5c38; }

.gold { color:#D4A017; }
.green { color:#0E7C4F; }
</style>
</head>
<body>

<header>
    <h2>KUVUNA</h2>
    <div>Dashboard Administrativo</div>
</header>

<nav>
    <button onclick="showPage('dashboard')">Dashboard</button>
    <button onclick="showPage('produtos')">Produtos</button>
    <button onclick="showPage('afiliados')">Afiliados</button>
    <button onclick="showPage('relatorios')">Relatórios</button>
    <button onclick="showPage('checkout')">Checkout</button>
    <button onclick="showPage('config')">Configurações</button>
</nav>

<main>

<!-- DASHBOARD -->
<div id="dashboard" class="page">
    <h2>Dashboard</h2>
    <div class="card">
        <h3>Vendas: <span class="gold">1.250.000 MZN</span></h3>
        <h3>Afiliados: <span class="green">520</span></h3>
        <h3>Ticket Médio: <span class="gold">450 MZN</span></h3>
        <canvas id="salesChart"></canvas>
    </div>
</div>

<!-- PRODUTOS -->
<div id="produtos" class="page hidden">
    <h2>Meus Produtos</h2>
    <div class="card">
        <button class="btn">Adicionar Produto</button>
        <ul>
            <li>Curso Marketing Digital - 500 MZN</li>
            <li>Ebook Empreendedorismo - 350 MZN</li>
        </ul>
    </div>
</div>

<!-- AFILIADOS -->
<div id="afiliados" class="page hidden">
    <h2>Afiliados</h2>
    <div class="card">
        <p>João - 70 vendas</p>
        <p>Maria - 55 vendas</p>
    </div>
</div>

<!-- RELATÓRIOS -->
<div id="relatorios" class="page hidden">
    <h2>Relatórios</h2>
    <div class="card">
        <canvas id="relatorioChart"></canvas>
    </div>
</div>

<!-- CHECKOUT -->
<div id="checkout" class="page hidden">
    <h2>Checkout</h2>
    <div class="card">
        <label>Produto:</label>
        <select>
            <option>Curso - 500 MZN</option>
            <option>Ebook - 350 MZN</option>
        </select>
        <br><br>
        <label>Pagamento:</label>
        <select>
            <option>M-Pesa</option>
            <option>e-Mola</option>
            <option>PayPal</option>
        </select>
        <br><br>
        <button class="btn" onclick="alert('Pagamento Simulado com Sucesso!')">Finalizar</button>
    </div>
</div>

<!-- CONFIGURAÇÕES -->
<div id="config" class="page hidden">
    <h2>Configurações</h2>
    <div class="card">
        <p>Comissão Plataforma: 10%</p>
        <p>Comissão Afiliados: 40% - 60%</p>
        <p>Moeda: MZN</p>
    </div>
</div>

</main>

<script>
function showPage(pageId){
    document.querySelectorAll('.page').forEach(p => p.classList.add('hidden'));
    document.getElementById(pageId).classList.remove('hidden');
}

new Chart(document.getElementById('salesChart'), {
    type:'line',
    data:{
        labels:['Jan','Fev','Mar','Abr','Mai','Jun'],
        datasets:[{
            label:'Vendas',
            data:[200000,300000,450000,600000,900000,1250000],
            borderColor:'#D4A017',
            backgroundColor:'rgba(212,160,23,0.2)',
            tension:0.4
        }]
    }
});

new Chart(document.getElementById('relatorioChart'), {
    type:'bar',
    data:{
        labels:['Produto A','Produto B','Produto C'],
        datasets:[{
            label:'Vendas',
            data:[120,90,60],
            backgroundColor:'#0E7C4F'
        }]
    }
});
</script>

</body>
</html>
