# BUG-001 — Sistema permite inserção de números e caracteres especiais no campo "Nome e Sobrenome"

## Informações

| Campo | Valor |
| :--- | :--- |
| **ID** | BUG-001 |
| **Módulo** | Fluxo de Assinatura (Checkout) |
| **Funcionalidade** | Preenchimento de Dados Cadastrais |
| **Severidade** | Média |
| **Prioridade** | Média |
| **Ambiente** | Produção (https://coffexapp.com/) |
| **Navegador** | Brave / Chrome |
| **Sistema Operacional** | Windows 11 |
| **Status** | Aberto |

---

## Descrição
Os campos de "Nome e Sobrenome" no formulário de checkout não possuem validação restritiva de caracteres, permitindo que o usuário insira números e emojis, que são salvos no estado do formulário.

---

## Pré-condições
* Usuário na etapa de finalização de compra (Checkout).
* Plano de assinatura selecionado e presente no carrinho.

---

## Passos para reprodução
1. Acessar a página de checkout.
2. Localizar o formulário de "Dados de Contato" ou "Endereço".
3. No campo "Nome" ou "Sobrenome", digitar um valor numérico (ex: `12345`) ou caracteres especiais/emojis (ex: `Lucas ☕`).
4. Clicar fora do campo para acionar a validação da interface.

---

## Resultado esperado
O sistema deve apresentar uma mensagem de erro de validação (ex: "Insira um nome válido") e impedir que caracteres não alfabéticos sejam mantidos no campo, garantindo a integridade dos dados cadastrais.

---

## Resultado obtido
O sistema aceita os números e caracteres especiais sem apresentar nenhum alerta de erro, mantendo o preenchimento inválido no formulário.

---

## Impacto
O impacto direto é a poluição do banco de dados da empresa com nomes inválidos, o que pode gerar falhas futuras na emissão de notas fiscais, relatórios de clientes ou personalização de e-mails de marketing.

---

## Evidências
![Evidência do Bug 001](../evidencias/bug001-evidencia.jpg)