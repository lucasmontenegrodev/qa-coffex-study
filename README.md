# QA Case Study — Coffex Clube

> Estudo de caso desenvolvido para demonstrar uma abordagem manual e exploratória de Quality Assurance aplicada ao fluxo de assinatura e checkout da plataforma Coffex.

## Sobre o projeto
Este repositório apresenta um planejamento e execução de testes funcionais realizados em um ambiente de produção (público). O objetivo é demonstrar a aplicação de práticas de QA em um cenário real de e-commerce, contemplando a elaboração de um plano estratégico, escrita de casos de teste estruturados, análise de requisições web e documentação técnica de vulnerabilidades.

Todos os testes foram realizados utilizando ferramentas de inspeção e dados fictícios, sem gerar ônus ou impactar a operação da plataforma. Este projeto possui finalidade exclusivamente educacional e composição de portfólio.

---

## Escopo Analisado
**Módulo:** Fluxo de Assinatura e Checkout

**Funcionalidades testadas:**
* Seleção de planos de assinatura.
* Transição de itens para o carrinho de compras.
* Validação de cálculo de frete via API de CEP.
* Validação e sanitização de formulários de dados cadastrais.
* Comportamento do Front-end e análise de requisições (Network).

**Fora do escopo:**
* Processamento financeiro real (Gateway de pagamentos).
* Área do assinante logado.

---

## Estrutura do Repositório

* `documentacao/`
  * `plano-de-testes.md`
  * `casos-de-teste.md`
* `reporte-de-bugs/`
  * `BUG-001-nome-aceita-numeros.md`
  * `BUG-002-injecao-html-campo-nome.md`
* `evidencias/`
  * `bug001-evidencia.jpg`
  * `bug002-evidencia-1.png`
  * `bug002-evidencia-2.png`

---

## Ferramentas Utilizadas
* Navegador (Brave / Google Chrome)
* Chrome DevTools (Aba Network para análise de requisições e HTTP Status Codes)
* Git e GitHub
* Markdown para documentação estruturada

---

## Resultados da Execução

| Métrica | Quantidade |
| :--- | :--- |
| **Casos de teste planejados** | 9 |
| **Casos de teste executados** | 9 |
| **Bugs documentados** | 2 |
| **Sessões exploratórias (Charters)** | 3 |

---

## Aviso de Isenção (Disclaimer)
Este projeto é um estudo independente. Não possui qualquer vínculo comercial, afiliação ou autorização prévia com a marca Coffex. As análises representam uma avaliação externa realizada estritamente em interfaces públicas da plataforma para fins de estudo em Engenharia de Qualidade.