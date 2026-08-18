# 📈 Simulador de Rendimentos & Independência Financeira Pro

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-323330?style=for-the-badge&logo=javascript&logoColor=F7DF1E)

Uma suíte web de alta fidelidade visual para simulação de juros compostos e cálculos de aposentadoria precoce. O design e a experiência do usuário (UX) foram construídos inspirados nas interfaces das maiores fintechs e corretoras do mercado (como Nubank, XP e BTG Pactual).

🌐 **Acesse a versão online:** [Calculadora Pro - ghf-br](https://ghf-br.github.io/simulador-rendimento/)

---

## 🧩 Módulos do Aplicativo

O sistema é dividido em duas ferramentas conectadas por um menu de navegação fluido:

### 1. Projeção de Juros (Calculadora de Ganho Garantido)
* Focada em responder: *"Quanto dinheiro terei no futuro?"*
* Apresenta um gráfico interativo de área empilhada (Chart.js) dividindo visualmente o valor "tirado do bolso" do "lucro puro dos juros".
* Tabela expansível com o detalhamento da evolução patrimonial ano a ano.

### 2. Meta de Renda (Independência Financeira)
* Focada em responder: *"Quando poderei viver de renda passiva?"*
* Utiliza cálculos matemáticos de logaritmo e engenharia reversa para descobrir o tempo exato (Anos e Meses) e o Montante Alvo necessários para gerar o salário mensal desejado pelo usuário.
* Apresenta a data futura estimada (Ex: "Junho de 2045") em que a meta será alcançada.

---

## 🚀 Funcionalidades Principais

Este projeto se comporta como um verdadeiro *Dashboard Financeiro* reativo:

* **Cálculo em Tempo Real:** Os resultados e o gráfico são atualizados instantaneamente conforme o usuário digita, sem a necessidade de clicar em botões de "Calcular".
* **Máscaras de Digitação:** Formatação automática e inteligente para moedas (R$) e porcentagens (%), trazendo uma experiência de uso premium.
* **Modo Escuro e Claro (Dark/Light Mode):** Alternância de temas fluida e animada, com paletas de cores estudadas para conforto visual.
* **Memória Inteligente (Local Storage):** Se a página for recarregada ou fechada, os últimos dados digitados em qualquer aba são salvos e restaurados automaticamente.
* **Exportação para PDF (Nativo):** Geração de relatórios profissionais direto para PDF, injetando cabeçalhos dinâmicos, escondendo painéis interativos e adaptando as cores para impressão em papel A4 sem distorções.

---

## 🛠️ Tecnologias Utilizadas

O projeto foi construído focando em altíssima performance e simplicidade, sem a necessidade de frameworks pesados:

* **HTML5:** Estruturação semântica.
* **CSS3:** Estilização avançada com Grid Layout, Flexbox, variáveis nativas (Custom Properties) e Media Queries específicas para impressão (`@media print`).
* **JavaScript (Vanilla):** Lógica de negócios, cálculos de logaritmo, controle de estado e manipulação do DOM.
* **[Chart.js](https://www.chartjs.org/):** Biblioteca para renderização de gráficos dinâmicos via HTML5 Canvas.
* **Google Fonts (Inter):** Tipografia padrão de mercado para interfaces financeiras modernas.

---

## 💻 Como usar localmente

Por ser uma aplicação baseada em arquitetura Front-end pura (Client-side), não há necessidade de instalar pacotes (`npm` ou `yarn`) ou configurar servidores locais.

1. Faça o clone deste repositório:
   ```bash
   git clone https://github.com/ghf-br/simulador-rendimento.git
