# Casos de Teste - Fluxo de Assinatura Coffex

## 1. Seleção de Plano

| ID | Cenário | Pré-condição | Dados de Teste | Resultado Esperado | Resultado Obtido | Status | Prioridade |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **CT-001** | Selecionar plano Cotidianos com sucesso | Usuário na página inicial do Coffex | N/A | O usuário deve ser redirecionado para a página do carrinho com o plano Cotidianos adicionado | Avanço ocorreu normalmente | Passou | Alta |
| **CT-002** | Selecionar plano Seleções com sucesso | Usuário na página inicial do Coffex | N/A | O usuário deve ser redirecionado para a página do carrinho com o plano Seleções adicionado | Avanço ocorreu normalmente | Passou | Alta |

---

## 2. Carrinho e Cálculo de Frete

| ID | Cenário | Pré-condição | Dados de Teste | Resultado Esperado | Resultado Obtido | Status | Prioridade |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **CT-003** | Calcular frete com CEP válido | Item adicionado ao carrinho | CEP: 01001-000 (São Paulo) | Sistema deve exibir o valor do frete e o prazo de entrega | O sistema validou corretamente | Passou | Alta |
| **CT-004** | Calcular frete com CEP inválido/incompleto | Item adicionado ao carrinho | CEP: 00000-00 | Sistema deve exibir mensagem de erro solicitando um CEP válido e impedir o avanço | O sistema exibiu a mensagem de erro | Passou | Média |
| **CT-005** | Calcular frete com CEP vazio | Item adicionado ao carrinho | CEP em branco | Sistema deve impedir o cálculo e solicitar o preenchimento | O sistema exibiu a mensagem de erro | Passou | Média |

---

## 3. Preenchimento de Dados Cadastrais

| ID | Cenário | Pré-condição | Dados de Teste | Resultado Esperado | Resultado Obtido | Status | Prioridade |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **CT-006** | Preencher formulário de contato com dados válidos | Usuário na etapa de dados cadastrais | Nome, E-mail válido, CPF válido, Celular | O sistema deve aceitar os dados cadastrais sem apresentar mensagens de erro de validação nestes campos. | O sistema validou corretamente | Passou | Alta |
| **CT-007** | Inserir E-mail com formato inválido | Usuário na etapa de dados cadastrais | E-mail: "teste@.com" ou "teste.com" | Sistema deve apontar erro de formatação no campo de e-mail | O sistema exibiu a mensagem de erro | Passou | Alta |
| **CT-008** | Inserir CPF incompleto | Usuário na etapa de dados cadastrais | CPF: 123.456.789-0 | Sistema deve apresentar erro de validação e não liberar o próximo passo | O sistema exibiu a mensagem de erro | Passou | Alta |
| **CT-009** | Tentar avançar sem preencher campos obrigatórios | Usuário na etapa de dados cadastrais | Todos os campos vazios | Sistema deve destacar os campos obrigatórios em vermelho e impedir o avanço | O sistema exibiu a mensagem de erro | Passou | Alta |
| **CT-010** | Inserir números e caracteres especiais no campo Nome | Usuário na etapa de dados cadastrais | Nome: "Lucas☕" | Sistema deve exibir erro indicando formato inválido e bloquear a entrada | O sistema aceitou a entrada sem exibir erro | Falhou (BUG-001) | Alta |
| **CT-011** | Inserir tags HTML (XSS) no campo Nome | Usuário na etapa de dados cadastrais | Nome: "<b>Lucas</b>" | Sistema deve sanitizar o texto ou bloquear o envio (exibindo erro) | O sistema enviou a tag, gerando erro 502 no Gateway | Falhou (BUG-002) | Alta |

---

## 4. Testes Exploratórios

### Charter 1 - Validação de Limites e Segurança Básica
*   **Objetivo:** Forçar os campos de formulário para encontrar quebras de layout ou falhas de validação.
*   **Explorar:**
    * Digitar milhares de caracteres no campo de Nome.
    * Copiar e colar emojis ou caracteres especiais não convencionais nos campos de texto.

### Charter 2 - Estresse de Interface e Navegação
*   **Objetivo:** Avaliar o comportamento do front-end sob ações inesperadas do usuário.
*   **Explorar:**
    * Clicar repetidamente e de forma rápida no botão de "Calcular Frete" ou avançar etapa para verificar se o sistema trava ou gera requisições duplicadas.
    * Recarregar a página (F5) no meio do preenchimento do formulário de endereço para validar se os dados são perdidos abruptamente.

### Charter 3 - Compatibilidade e Responsividade
*   **Objetivo:** Identificar problemas de interação visual no carrinho de compras e        formulários.
*   **Explorar:**
    * Redimensionar a janela do navegador para simular o tamanho de uma tela de celular.
    * Tentar navegar pelos campos do formulário apenas utilizando a tecla `Tab` do teclado.