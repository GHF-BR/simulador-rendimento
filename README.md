# 📈 Calculadora de Ganho Garantido Pro

Uma aplicação web de alta fidelidade visual para simulação de juros compostos e projeção patrimonial. O design e a experiência do usuário (UX) foram construídos inspirados nas interfaces das maiores fintechs e corretoras do mercado (como Nubank, XP e BTG Pactual).

🌐 **Acesse a versão online:** [Calculadora Pro - ghf-br](https://ghf-br.github.io/simulador-rendimento/)

---

## 🚀 Funcionalidades

Este projeto não é apenas uma calculadora, mas um verdadeiro *Dashboard Financeiro* com comportamento reativo:

* **Cálculo em Tempo Real:** Os resultados e o gráfico são atualizados instantaneamente conforme o usuário digita, sem a necessidade de clicar em botões de "Calcular".
* **Gráfico Interativo (Chart.js):** Projeção visual de área empilhada, dividindo claramente o que é o dinheiro "tirado do bolso" e o que é o "lucro puro dos juros".
* **Máscaras de Digitação:** Formatação automática e inteligente para moedas (R$) e porcentagens (%), trazendo uma experiência de uso premium.
* **Modo Escuro e Claro (Dark/Light Mode):** Alternância de temas fluida e animada, respeitando a preferência do usuário.
* **Memória Inteligente (Local Storage):** Se a página for recarregada ou fechada, os últimos dados digitados são salvos e restaurados automaticamente.
* **Tabela de Evolução:** Uma seção expansível que mostra os detalhes numéricos da evolução do patrimônio ano a ano.
* **Exportação para PDF (Nativo):** Geração de relatórios limpos, formatados para papel A4, escondendo os controles interativos e focando exclusivamente nos dados da simulação.

## 🛠️ Tecnologias Utilizadas

O projeto foi construído focando em performance e simplicidade, sem a necessidade de frameworks pesados:

* **HTML5:** Estruturação semântica.
* **CSS3:** Estilização com Grid Layout, Flexbox, variáveis nativas (Custom Properties) e Media Queries para responsividade total e impressão (`@media print`).
* **JavaScript (Vanilla):** Lógica de negócios, cálculos financeiros e manipulação do DOM.
* **[Chart.js](https://www.chartjs.org/):** Biblioteca para renderização de gráficos modernos via HTML5 Canvas.
* **Google Fonts (Inter):** Tipografia padrão de mercado para interfaces financeiras.

## 💻 Como usar localmente

Por ser uma aplicação baseada em HTML/CSS/JS puros, não há necessidade de instalar pacotes (`npm` ou `yarn`) ou configurar servidores locais.

1. Faça o clone deste repositório:
   ```bash
   git clone [https://github.com/ghf-br/simulador-rendimento.git](https://github.com/ghf-br/simulador-rendimento.git)

```

2. Abra a pasta do projeto.
3. Dê um duplo clique no arquivo `index.html` para abri-lo diretamente em qualquer navegador moderno.

---

## 📄 Código Fonte (`index.html`)

Caso queira replicar o projeto em um único arquivo, basta copiar o código abaixo e salvar como `index.html`:

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculadora de Ganho Garantido Pro</title>
    
    <!-- Fonte Inter -->
    <link rel="preconnect" href="[https://fonts.googleapis.com](https://fonts.googleapis.com)">
    <link rel="preconnect" href="[https://fonts.gstatic.com](https://fonts.gstatic.com)" crossorigin>
    <link href="[https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap](https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap)" rel="stylesheet">
    
    <!-- Chart.js para o Gráfico -->
    <script src="[https://cdn.jsdelivr.net/npm/chart.js](https://cdn.jsdelivr.net/npm/chart.js)"></script>

    <style>
        :root {
            --bg-color: #121214;
            --surface-color: #202024;
            --surface-hover: #29292e;
            --primary: #820ad1; 
            --success: #04d361; 
            --text-main: #e1e1e6;
            --text-muted: #a8a8b3;
            --border-color: #323238;
            --chart-grid: #323238;
        }

        body.light-theme {
            --bg-color: #f4f6f9;
            --surface-color: #ffffff;
            --surface-hover: #f8f9fa;
            --primary: #820ad1;
            --success: #05a04c;
            --text-main: #212529;
            --text-muted: #6c757d;
            --border-color: #dee2e6;
            --chart-grid: #e9ecef;
        }

        body {
            font-family: 'Inter', sans-serif;
            background-color: var(--bg-color);
            color: var(--text-main);
            margin: 0;
            padding: 20px;
            display: flex;
            justify-content: center;
            min-height: 100vh;
            box-sizing: border-box;
            transition: background-color 0.3s, color 0.3s;
        }

        .dashboard-container {
            display: grid;
            grid-template-columns: 1fr;
            gap: 24px;
            max-width: 1000px;
            width: 100%;
            align-content: start;
        }

        @media (min-width: 768px) {
            .dashboard-container { grid-template-columns: 350px 1fr; }
        }

        .card {
            background: var(--surface-color);
            padding: 30px;
            border-radius: 16px;
            border: 1px solid var(--border-color);
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
        }

        .header-top { display: flex; justify-content: space-between; align-items: flex-start; grid-column: 1 / -1; }
        .header-title h1 { font-size: 28px; margin: 0 0 8px 0; font-weight: 700; }
        .header-title p { color: var(--text-muted); margin: 0; font-size: 15px; }

        .btn-theme {
            background: var(--surface-color); border: 1px solid var(--border-color);
            color: var(--text-main); font-size: 20px; cursor: pointer; padding: 10px;
            border-radius: 12px; display: flex; justify-content: center; align-items: center;
        }

        .input-group { margin-bottom: 24px; }
        label { display: block; font-weight: 500; margin-bottom: 10px; font-size: 14px; color: var(--text-main); }
        .input-wrapper { position: relative; display: flex; align-items: center; }
        .prefix { position: absolute; left: 14px; color: var(--text-muted); font-weight: 500; }
        
        input {
            width: 100%; background-color: var(--bg-color); color: var(--text-main);
            padding: 14px 14px 14px 40px; border: 1px solid var(--border-color);
            border-radius: 10px; font-size: 16px; font-family: 'Inter', sans-serif; box-sizing: border-box;
        }
        input.no-prefix { padding-left: 14px; }
        input:focus { border-color: var(--primary); outline: none; }

        .years-presets { display: grid; grid-template-columns: repeat(3, 1fr); gap: 10px; margin-bottom: 15px; }
        .btn-preset {
            background-color: var(--bg-color); color: var(--text-muted); border: 1px solid var(--border-color);
            padding: 12px; border-radius: 8px; cursor: pointer; font-weight: 600; font-size: 14px;
        }
        .btn-preset.active { background-color: rgba(130, 10, 209, 0.15); color: var(--primary); border-color: var(--primary); }

        .results-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(180px, 1fr)); gap: 16px; margin-bottom: 24px; }
        .result-box { background: var(--bg-color); border: 1px solid var(--border-color); padding: 20px; border-radius: 12px; }
        .result-box.highlight { background: linear-gradient(145deg, var(--surface-color), var(--bg-color)); border: 1px solid var(--primary); }
        
        .result-title { font-size: 13px; color: var(--text-muted); margin-bottom: 8px; font-weight: 500; }
        .result-value { font-size: 24px; font-weight: 700; color: var(--text-main); }
        .result-value.success { color: var(--success); }
        .result-value.primary { color: var(--primary); }

        .chart-container { position: relative; height: 350px; width: 100%; margin-bottom: 24px;}

        .btn-export {
            width: 100%; background-color: var(--primary); color: white;
            border: none; padding: 16px; font-size: 15px; font-weight: 600;
            border-radius: 10px; cursor: pointer; display: flex; justify-content: center; gap: 8px;
        }

        details { background: var(--bg-color); border: 1px solid var(--border-color); border-radius: 12px; padding: 15px; margin-top: 20px; }
        summary { font-weight: 600; cursor: pointer; color: var(--primary); font-size: 15px; outline: none;}
        .table-container { margin-top: 15px; overflow-x: auto; }
        table { width: 100%; border-collapse: collapse; text-align: left; font-size: 14px; }
        th, td { padding: 10px; border-bottom: 1px solid var(--border-color); color: var(--text-main); }

        .dev-footer { grid-column: 1 / -1; text-align: center; padding: 20px 0; font-size: 13px; color: var(--text-muted); }
        .dev-footer strong { color: var(--primary); }

        /* =========================================================
           CSS EXCLUSIVO PARA IMPRESSÃO/PDF
           ========================================================= */
        @media print {
            body, .dashboard-container, .card, .result-box, details {
                background: white !important;
                color: black !important;
                box-shadow: none !important;
            }
            
            .controls, .btn-theme, .header-title p, summary, .dev-footer {
                display: none !important;
            }

            .dashboard-container { display: block !important; padding: 0 !important; }
            .card.results { border: none !important; padding: 0 !important; }
            .header-title h1 { font-size: 24px !important; text-align: center; margin-bottom: 30px !important; color: #820ad1 !important; }
            .result-box { border: 1px solid #ddd !important; }

            .result-title { color: #555 !important; }
            .result-value { color: black !important; }
            .result-value.success { color: #05a04c !important; }
            .result-value.primary { color: #820ad1 !important; }

            details { border: none !important; }
            .table-container { display: block !important; }
            th, td { color: black !important; border-bottom: 1px solid #eee !important; }
            th { background-color: #f9f9f9 !important; font-weight: bold !important; }

            .chart-container { height: 280px !important; margin-bottom: 40px !important; page-break-inside: avoid; }
            * { -webkit-print-color-adjust: exact !important; print-color-adjust: exact !important; }
        }
    </style>
</head>
<body>

<div class="dashboard-container">
    
    <div class="header-top">
        <div class="header-title">
            <h1>📈 Relatório de Investimentos</h1>
            <p>Simulação avançada de projeção patrimonial e juros compostos.</p>
        </div>
        <button class="btn-theme" id="btnTheme" onclick="toggleTheme()" title="Alternar Tema">☀️</button>
    </div>

    <!-- Painel Lateral de Controles -->
    <div class="card controls">
        
        <div class="input-group">
            <label for="valorInicial">Valor Inicial (Já investido)</label>
            <div class="input-wrapper">
                <span class="prefix">R$</span>
                <input type="text" inputmode="numeric" id="valorInicial" class="mascara-moeda" value="0,00">
            </div>
        </div>

        <div class="input-group">
            <label for="aporte">Aporte Mensal</label>
            <div class="input-wrapper">
                <span class="prefix">R$</span>
                <input type="text" inputmode="numeric" id="aporte" class="mascara-moeda" value="500,00">
            </div>
        </div>

        <div class="input-group">
            <label for="taxa">Rentabilidade Anual</label>
            <div class="input-wrapper">
                <span class="prefix">%</span>
                <input type="text" inputmode="decimal" id="taxa" class="mascara-taxa" value="10,5">
            </div>
        </div>

        <div class="input-group">
            <label>Horizonte de Investimento</label>
            <div class="years-presets">
                <button class="btn-preset" onclick="setAnos(10, this)">10 Anos</button>
                <button class="btn-preset active" onclick="setAnos(20, this)">20 Anos</button>
                <button class="btn-preset" onclick="setAnos(30, this)">30 Anos</button>
            </div>
            <div class="input-wrapper">
                <input type="text" inputmode="numeric" id="anos" class="no-prefix mascara-numero" value="20">
            </div>
        </div>
        
        <button class="btn-export" onclick="gerarPDF()">
            📄 Gerar PDF Nativo
        </button>

    </div>

    <!-- Painel Principal de Resultados -->
    <div class="card results">
        
        <div class="results-grid">
            <div class="result-box">
                <div class="result-title">Valor Investido (Bolso)</div>
                <div class="result-value" id="totalInvestido">R$ 0,00</div>
            </div>
            <div class="result-box">
                <div class="result-title">Rendimento (Juros)</div>
                <div class="result-value success" id="totalLucro">R$ 0,00</div>
            </div>
            <div class="result-box highlight">
                <div class="result-title">Patrimônio Acumulado</div>
                <div class="result-value primary" id="saldoFinal">R$ 0,00</div>
            </div>
        </div>

        <div class="chart-container">
            <canvas id="graficoProjecao"></canvas>
        </div>

        <!-- Tabela Expansível -->
        <details id="tabelaDetalhes">
            <summary>Ver tabela de evolução ano a ano</summary>
            <div class="table-container">
                <table>
                    <thead>
                        <tr>
                            <th>Ano</th>
                            <th>Total Investido</th>
                            <th>Juros Acumulados</th>
                            <th>Saldo Total</th>
                        </tr>
                    </thead>
                    <tbody id="tabelaCorpo">
                        <!-- Linhas geradas via JS -->
                    </tbody>
                </table>
            </div>
        </details>
    </div>

    <!-- Assinatura -->
    <div class="dev-footer">
        Developed by <strong>GHF</strong>
    </div>

</div>

<script>
    let meuGrafico = null;

    function toggleTheme() {
        const isLight = document.body.classList.toggle('light-theme');
        document.getElementById('btnTheme').innerText = isLight ? '🌙' : '☀️';
        localStorage.setItem('theme_GHF', isLight ? 'light' : 'dark');
        calcularJuros(); 
    }

    function carregarTema() {
        const theme = localStorage.getItem('theme_GHF');
        if (theme === 'light') {
            document.body.classList.add('light-theme');
            document.getElementById('btnTheme').innerText = '🌙';
        }
    }

    function gerarPDF() {
        document.getElementById('tabelaDetalhes').open = true;
        const tituloOriginal = document.title;
        document.title = "Relatorio_Investimentos";
        window.print();
        document.title = tituloOriginal;
    }

    function aplicarMascaraMoeda(e) {
        let valor = e.target.value.replace(/\D/g, ''); 
        if (valor === '') valor = '0';
        valor = (parseInt(valor, 10) / 100).toFixed(2) + '';
        valor = valor.replace('.', ',');
        valor = valor.replace(/(\d)(?=(\d{3})+(?!\d))/g, '$1.');
        e.target.value = valor;
        salvarDados(); calcularJuros();
    }

    function aplicarMascaraTaxa(e) {
        let valor = e.target.value.replace(/[^0-9,]/g, '');
        e.target.value = valor;
        salvarDados(); calcularJuros();
    }

    function aplicarMascaraNumero(e) {
        let valor = e.target.value.replace(/\D/g, '');
        e.target.value = valor;
        salvarDados(); calcularJuros(); limparPresets();
    }

    document.getElementById('valorInicial').addEventListener('input', aplicarMascaraMoeda);
    document.getElementById('aporte').addEventListener('input', aplicarMascaraMoeda);
    document.getElementById('taxa').addEventListener('input', aplicarMascaraTaxa);
    document.getElementById('anos').addEventListener('input', aplicarMascaraNumero);

    function extrairNumero(id) {
        let stringVal = document.getElementById(id).value;
        if (!stringVal) return 0;
        stringVal = stringVal.replace(/\./g, '').replace(',', '.');
        return parseFloat(stringVal) || 0;
    }

    function salvarDados() {
        const dados = {
            valorInicial: document.getElementById('valorInicial').value,
            aporte: document.getElementById('aporte').value,
            taxa: document.getElementById('taxa').value,
            anos: document.getElementById('anos').value
        };
        localStorage.setItem('dadosFintechPro', JSON.stringify(dados));
    }

    function carregarDados() {
        const dadosSalvos = localStorage.getItem('dadosFintechPro');
        if (dadosSalvos) {
            const dados = JSON.parse(dadosSalvos);
            if(dados.valorInicial) document.getElementById('valorInicial').value = dados.valorInicial;
            if(dados.aporte) document.getElementById('aporte').value = dados.aporte;
            if(dados.taxa) document.getElementById('taxa').value = dados.taxa;
            if(dados.anos) document.getElementById('anos').value = dados.anos;
            
            const botoes = document.querySelectorAll('.btn-preset');
            botoes.forEach(b => {
                if(b.innerText.includes(dados.anos)) { b.classList.add('active'); } 
                else { b.classList.remove('active'); }
            });
        }
    }

    function setAnos(valor, botao) {
        document.getElementById('anos').value = valor;
        const botoes = document.querySelectorAll('.btn-preset');
        botoes.forEach(b => b.classList.remove('active'));
        botao.classList.add('active');
        salvarDados(); calcularJuros();
    }

    function limparPresets() {
        const botoes = document.querySelectorAll('.btn-preset');
        botoes.forEach(b => b.classList.remove('active'));
    }

    const formatarMoeda = (valor) => {
        return valor.toLocaleString('pt-BR', { style: 'currency', currency: 'BRL' });
    };

    function calcularJuros() {
        const valorInicial = extrairNumero('valorInicial');
        const aporteMensal = extrairNumero('aporte');
        const taxaAnual = extrairNumero('taxa') / 100;
        const anos = parseInt(document.getElementById('anos').value) || 1;
        
        const taxaMensal = Math.pow(1 + taxaAnual, 1 / 12) - 1;
        
        let saldoAcumulado = valorInicial;
        let totalInvestido = valorInicial;
        
        let historicoAnos = [];
        let dadosInvestido = [];
        let dadosJuros = [];
        
        const tabelaCorpo = document.getElementById('tabelaCorpo');
        tabelaCorpo.innerHTML = ''; 
        
        for (let ano = 1; ano <= anos; ano++) {
            for (let mes = 1; mes <= 12; mes++) {
                let rendimento = saldoAcumulado * taxaMensal;
                saldoAcumulado += aporteMensal + rendimento;
                totalInvestido += aporteMensal;
            }
            
            let jurosNoAno = saldoAcumulado - totalInvestido;
            
            historicoAnos.push(ano + 'º Ano');
            dadosInvestido.push(totalInvestido);
            dadosJuros.push(jurosNoAno);

            let tr = document.createElement('tr');
            tr.innerHTML = `
                <td>Ano ${ano}</td>
                <td>${formatarMoeda(totalInvestido)}</td>
                <td style="color: var(--success);">${formatarMoeda(jurosNoAno)}</td>
                <td style="font-weight: bold; color: var(--primary);">${formatarMoeda(saldoAcumulado)}</td>
            `;
            tabelaCorpo.appendChild(tr);
        }
        
        const lucroPuro = saldoAcumulado - totalInvestido;
        
        document.getElementById('totalInvestido').innerText = formatarMoeda(totalInvestido);
        document.getElementById('totalLucro').innerText = formatarMoeda(lucroPuro);
        document.getElementById('saldoFinal').innerText = formatarMoeda(saldoAcumulado);
        
        atualizarGrafico(historicoAnos, dadosInvestido, dadosJuros);
    }

    function atualizarGrafico(labels, investido, juros) {
        const ctx = document.getElementById('graficoProjecao').getContext('2d');
        
        const estiloCorpo = getComputedStyle(document.body);
        const corTexto = estiloCorpo.getPropertyValue('--text-muted').trim();
        const corGrid = estiloCorpo.getPropertyValue('--chart-grid').trim();
        
        Chart.defaults.color = corTexto;
        Chart.defaults.font.family = "'Inter', sans-serif";

        if (meuGrafico) meuGrafico.destroy();
        
        meuGrafico = new Chart(ctx, {
            type: 'line', 
            data: {
                labels: labels,
                datasets: [
                    {
                        label: 'Valor Investido',
                        data: investido,
                        borderColor: '#820ad1',
                        backgroundColor: 'rgba(130, 10, 209, 0.4)',
                        fill: true,
                        tension: 0.4,
                        pointRadius: 0,
                        pointHitRadius: 10
                    },
                    {
                        label: 'Juros Acumulados',
                        data: juros,
                        borderColor: '#04d361',
                        backgroundColor: 'rgba(4, 211, 97, 0.4)',
                        fill: true,
                        tension: 0.4,
                        pointRadius: 0,
                        pointHitRadius: 10
                    }
                ]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                animation: { duration: 500 }, 
                interaction: { mode: 'index', intersect: false },
                plugins: {
                    legend: { position: 'top', labels: { usePointStyle: true, boxWidth: 8, color: corTexto } },
                    tooltip: {
                        backgroundColor: '#202024', titleColor: '#e1e1e6', bodyColor: '#e1e1e6',
                        borderColor: '#323238', borderWidth: 1, padding: 12,
                        callbacks: {
                            label: function(context) { return context.dataset.label + ': ' + formatarMoeda(context.raw); }
                        }
                    }
                },
                scales: {
                    x: { grid: { display: false, drawBorder: false }, ticks: { color: corTexto } },
                    y: {
                        stacked: true, 
                        grid: { color: corGrid, drawBorder: false },
                        ticks: {
                            color: corTexto,
                            callback: function(value) {
                                if (value >= 1000000) return 'R$ ' + (value / 1000000).toFixed(1) + 'M';
                                if (value >= 1000) return 'R$ ' + (value / 1000).toFixed(0) + 'k';
                                return 'R$ ' + value;
                            }
                        }
                    }
                }
            }
        });
    }

    window.addEventListener('beforeprint', () => {
        if(meuGrafico) {
            meuGrafico.options.scales.x.ticks.color = '#000';
            meuGrafico.options.scales.y.ticks.color = '#000';
            meuGrafico.options.plugins.legend.labels.color = '#000';
            meuGrafico.update();
        }
    });

    window.addEventListener('afterprint', () => {
        calcularJuros(); 
    });
    
    window.onload = function() {
        carregarTema();
        carregarDados();
        calcularJuros();
    };
</script>

</body>
</html>

```

---

**Autor:** Desenvolvido por **GHF**

```

```
