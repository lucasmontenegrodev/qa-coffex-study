# Plano de Testes — Coffex (Fluxo de Assinatura)

## 1. Informações Gerais

| Item | Valor |
| :--- | :--- |
| **Projeto** | QA Case Study - Coffex Clube |
| **Módulo** | Fluxo de Assinatura (Checkout Público) |
| **Responsável** | Lucas Montenegro |
| **Versão** | 1.0 |
| **Data** | 17/07/2026 |

---

## 2. Objetivo
Garantir a qualidade e o funcionamento adequado da jornada de assinatura de planos de café (Cotidianos e Seleções) na plataforma Coffex, validando regras de negócio do carrinho, cálculo de frete e integridade dos formulários de cadastro.

---

## 3. Escopo

**O que será testado (In Scope):**
* Seleção dos planos de assinatura (Cotidianos e Seleções).
* Transição dos itens selecionados para o carrinho de compras.
* Validação do cálculo de frete inserindo diferentes formatos de CEP.
* Preenchimento dos formulários de dados cadastrais.
* Validação de campos obrigatórios e tratamento de erros de digitação (ex: e-mail inválido, CPF incompleto).

**O que NÃO será testado (Out of Scope):**
* Processamento real do pagamento (integração com gateway de cartão).
* Área do assinante logado (pois requer uma assinatura ativa paga).
* Testes de carga, stress, performance ou vulnerabilidade de segurança.

---

## 4. Estratégia de Testes
A execução focará em simular a jornada real de um novo cliente no site. Serão aplicadas as seguintes abordagens:
* **Testes Funcionais:** Validação do caminho feliz e fluxos alternativos da jornada de assinatura.
* **Testes de Validação de Campos:** Verificação de limites de caracteres, campos numéricos e máscaras de dados (CPF, CEP, Celular) nos formulários de cadastro.
* **Testes Exploratórios:** Sessões livres focadas em usabilidade, quebra de fluxo (recarregar página, avançar e voltar etapas) e layout básico.

---

## 5. Ambiente

| Item | Valor |
| :--- | :--- |
| **Sistema Operacional** | Windows 11 |
| **Navegador** | Brave / Chrome |
| **Ambiente de Teste** | Produção (URL Pública) |
| **URL Base** | https://coffexapp.com/ |

----

## 6. Critérios de Entrada e Saída

**Critérios de Entrada (Entry Criteria):**
* A plataforma Coffex deve estar acessível pelo navegador.
* O fluxo de seleção de planos e transição para o checkout deve estar liberado para usuários anônimos.
* Ferramentas de inspeção (DevTools) disponíveis para análise técnica.

**Critérios de Saída (Exit Criteria):**
* 100% dos casos de teste planejados executados.
* Todos os comportamentos inesperados documentados como Bugs, classificados por severidade.
* Documentação de evidências (prints ou descrições) anexada aos resultados.

---

## 7. Riscos Mapeados

| Risco | Impacto | Prioridade |
| :--- | :--- | :--- |
| **Cálculo de Frete Incorreto:** Sistema não processar CEPs válidos, impedindo a finalização da compra. | Alto | Alta |
| **Validação de Cadastro Falha:** Sistema aceitar dados incorretos (como CPF com letras), poluindo o banco de dados. | Alto | Alta |
| **Quebra de Navegação:** Botões de "Avançar" ou "Voltar" não funcionarem durante o preenchimento do formulário. | Médio | Alta |
| **Falha de Layout (Responsividade):** Elementos da tela se sobreporem em telas menores, dificultando a leitura. | Baixo | Média |

---

## 8. Critérios de Priorização

Caso haja restrição de tempo, os testes serão executados seguindo a ordem de criticidade abaixo:

1. Fluxo principal de assinatura (Caminho Feliz).
2. Validações obrigatórias de formulário (Dados de contato e endereço).
3. Cálculo de frete (Integração de CEP).
4. Cenários negativos (Tentativas de avanço com dados inválidos).
5. Navegação e Usabilidade básica.

---

## 9. Entregáveis

Ao final do ciclo de testes, os seguintes artefatos estarão disponíveis neste repositório:

* Plano de Testes (Este documento).
* Documentação de Casos de Teste.
* Relatórios de Bugs documentados (com evidências).
* Scripts de Automação (Playwright com Python).