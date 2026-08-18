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

 Desenvolvido por **GHF**
