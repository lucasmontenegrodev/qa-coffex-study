# BUG-002 — Sistema permite injeção de tags HTML no campo "Nome e Sobrenome"

## Informações

| Campo | Valor |
| :--- | :--- |
| **ID** | BUG-002 |
| **Módulo** | Fluxo de Assinatura (Checkout) |
| **Funcionalidade** | Preenchimento de Dados Cadastrais |
| **Severidade** | Alta |
| **Prioridade** | Alta |
| **Ambiente** | Produção (https://coffexapp.com/) |
| **Navegador** | Brave / Chrome |
| **Sistema Operacional** | Windows 11 |
| **Status** | Aberto |

---

## Descrição
O campo de "Nome e Sobrenome" não realiza a sanitização de caracteres especiais voltados para marcação de texto (tags HTML). Isso cria uma brecha para vulnerabilidades de segurança, como XSS (Cross-Site Scripting), ou quebra de layout caso os dados sejam renderizados sem tratamento em outras telas do sistema (como painéis administrativos).

> **Nota de Execução Técnica:** Durante os testes em ambiente de Produção, a validação de persistência desta injeção HTML no Back-end (Banco de Dados) foi bloqueada. A requisição final (`POST` para o endpoint `/card`) retornou um Status Code `502 (Bad Gateway)`, pois o gateway de pagamento (Pagar.me) recusou o cartão de crédito gerado para o teste, interrompendo o fluxo antes da gravação dos dados cadastrais. Portanto, este reporte foca estritamente na vulnerabilidade de sanitização da camada de Front-end.

---

## Pré-condições
* Usuário na etapa de checkout.
* Formulário de dados cadastrais disponível para preenchimento.

---

## Passos para reprodução
1. Acessar a página de checkout.
2. Clicar no campo "Nome e Sobrenome".
3. Inserir um texto contendo tags HTML básicas, como `<b>Teste de XSS</b>` ou `<script>alert('Teste')</script>`.
4. Clicar fora do campo para acionar as validações de *Front-end*.

---

## Resultado esperado
O sistema deve sanitizar a entrada (remover as tags automaticamente) ou apresentar uma mensagem de erro de validação informando que caracteres especiais não são permitidos, impedindo a injeção do código.

---

## Resultado obtido
O sistema aceita a tag HTML sem apresentar nenhum alerta, mantendo a formatação indesejada no estado do formulário.

---

## Impacto
Risco de segurança. A falta de sanitização no cliente pode refletir em vulnerabilidades no Back-end, permitindo a execução de scripts maliciosos ou a quebra de estrutura visual na área de gestão de clientes da plataforma.

---

## Recomendação de Investigação
Devido à impossibilidade de ultrapassar a barreira de validação do gateway de pagamento (Pagar.me) utilizando cartões de teste no ambiente de Produção (retorno 502 Bad Gateway), a validação da persistência desta injeção não pôde ser concluída. 

**Ação sugerida:** Solicita-se à equipe de engenharia a execução deste mesmo cenário em ambiente de Homologação/QA, preferencialmente disparando a requisição de payload diretamente via API (ex: Postman), para verificar se a camada de Back-end e o banco de dados também estão vulneráveis à falta de sanitização (XSS).

---

## Evidências
![Evidência do Bug 002](../evidencias/bug002-evidencia.png)