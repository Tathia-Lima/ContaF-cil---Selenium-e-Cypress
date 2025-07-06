# Clone Local - ContaFácil

Esta é uma versão local da aplicação web "ContaFácil", desenvolvida para fins de estudo e execução offline.

## Pré-requisitos

*   **Python 3:** Certifique-se de ter o Python 3 instalado em sua máquina. Você pode baixá-lo em [python.org](https://www.python.org/).
*   **Pip:** O gerenciador de pacotes do Python, geralmente incluído na instalação do Python.

## Configuração e Instalação

1.  **Descompacte o arquivo:** Extraia o conteúdo do arquivo `ContaFacil_local.zip` para uma pasta de sua preferência.
2.  **Navegue até o diretório:** Abra o terminal ou prompt de comando e navegue até a pasta `ContaFacil_local` que você acabou de extrair.
    ```bash
    cd caminho/para/ContaFacil_local
    ```
3.  **(Opcional, mas recomendado) Crie um Ambiente Virtual:** Isso isola as dependências do projeto.
    ```bash
    python -m venv venv 
    ```
4.  **(Opcional) Ative o Ambiente Virtual:**
    *   **Linux/macOS:** `source venv/bin/activate`
    *   **Windows:** `venv\Scripts\activate`
5.  **Instale as dependências:** Execute o comando abaixo para instalar o Flask e suas dependências.
    ```bash
    pip install -r requirements.txt
    ```

## Executando a Aplicação

1.  **Inicie o servidor:** No mesmo terminal (com o ambiente virtual ativado, se você o criou), execute:
    ```bash
    python app.py
    ```
2.  **Acesse no navegador:** Abra seu navegador de internet e acesse o endereço:
    [http://127.0.0.1:5000](http://127.0.0.1:5000)

## Funcionalidades

A aplicação permite:
*   Cadastrar novos usuários.
*   Fazer login com usuários existentes.
*   Adicionar e listar contas bancárias.
*   Excluir contas (isso também excluirá as movimentações associadas).
*   Criar movimentações financeiras (receitas e despesas).
*   Visualizar um resumo mensal das movimentações.
*   Excluir movimentações individuais.
*   Fazer logout.
*   **Resetar Dados:** Acessar a rota `/reset` (ex: http://127.0.0.1:5000/reset) enquanto logado limpará todas as contas e movimentações do usuário atual (útil para testes).

## Banco de Dados

*   Os dados (usuários, contas, movimentações) são armazenados em um arquivo chamado `database.db` dentro da pasta `ContaFacil_local`.
*   Este arquivo será criado automaticamente na primeira vez que você executar a aplicação, caso ele não exista.

## Observações

*   Esta é uma versão simplificada baseada na análise da aplicação original. Algumas funcionalidades complexas ou detalhes visuais podem diferir.
*   A funcionalidade de *editar conta* possui a lógica no backend, mas não foi implementada uma tela específica no frontend (a rota `/contas/editar/<id>` existe, mas redireciona para a listagem).
*   A aplicação foi desenvolvida para rodar localmente e não possui as mesmas medidas de segurança de uma aplicação web de produção.




# 🧪✨ CONTAFÁCIL - TESTES AUTOMATIZADOS COM SELENIUM WEBDRIVER✨

Este diretório contém os testes automatizados para o aplicativo web **ContaFácil**, desenvolvidos com **JavaScript**, **Selenium WebDriver**, **Mocha** e **Chai**.

---

## 🔴 ➡️ PRÉ-REQUISITOS

Antes de executar os testes, verifique se você possui:

### ✅ **Node.js e npm**
- Verifique a instalação:
  ```bash
  node -v
  npm -v
  ```
- Caso não tenha, acesse: [https://nodejs.org](https://nodejs.org) e instale.

### ✅ **Navegador Web**
- **Google Chrome** (recomendado).

### ✅ **ChromeDriver**
- A versão do **ChromeDriver** deve ser **compatível** com a versão do seu Chrome.
- Verifique a versão do seu Chrome acessando:
  ```
  chrome://version
  ```
- Faça o download correspondente:  
  [https://chromedriver.chromium.org/downloads](https://chromedriver.chromium.org/downloads)

📌 **IMPORTANTE:**  
Coloque o `chromedriver.exe`:
- **Preferencialmente:** em um diretório incluso no `PATH` do sistema.  
- **Ou:** na **mesma pasta raiz** do projeto (ex: `contafacil_selenium_tests_js`).

---

## 🔴 ➡️ CONFIGURAÇÃO DO AMBIENTE

1. Acesse o diretório raiz do projeto:

   ```bash
   cd C:\caminho\para\sua\pasta\contafacil_selenium_tests_js
   ```

2. Instale as dependências:

   ```bash
   npm install
   ```

   Isso instalará **Selenium WebDriver**, **Mocha** e **Chai**.

---


## 🔴 ➡️ EXECUTANDO O APLICATIVO CONTAFÁCIL (BACKEND)

Certifique-se de que o **aplicativo Flask** esteja em execução:  
```
http://localhost:5000
```

---

## 🔴 ➡️ EXECUTANDO OS TESTES

No terminal, acesse o diretório raiz do projeto:

```bash
cd C:\caminho\para\sua\pasta\contafacil_selenium_tests_js
```

Execute os testes com:

```bash
npm test
```

Você verá os testes sendo executados no navegador Chrome e os resultados no terminal, *se o ChromeDriver e o Chrome forem compatíveis*.

---

## 🔴 ➡️ PERSONALIZAÇÃO E OBSERVAÇÕES IMPORTANTES

### 🧩 **Modo Headless**
- Para rodar os testes sem abrir o navegador:
  - Descomente a linha:
    ```js
    chromeOptions.addArguments('--headless');
    ```
  - Essa linha está dentro do `beforeEach` em `e2e/editar_movimentacao.spec.js`.

### 🌐 **URL Base**
- Alterar a URL base se seu app não estiver rodando no `http://localhost:5000`.

### 🔐 **Credenciais de Teste**
- As variáveis `USER_EMAIL` e `USER_PASSWORD` devem estar corretas e apontar para um usuário **existente** no banco de dados.

### 📌 **Dados de Teste**
- Certifique-se de que as **Contas "Conta 3" e "Conta 2"** existam e possuam movimentações criadas para o usuário de teste.

### 🧼 **Reset do Estado**
Para garantir que os testes sejam **reprodutíveis**, crie um endpoint no seu backend para limpar os dados de teste:

```http
POST /reset
```

### 🗓️ **Validação de Datas**
- Datas são geradas com `new Date()` no JavaScript.
- Ajustes podem ser necessários caso haja validações rígidas no backend relacionadas a *fuso horário* ou *data atual*.

### 📢 **Mensagens Flash**
- Capturadas por:
  ```js
  LoginPage.getAlertMessageText()
  EditMovimentacaoPage.validarMensagem()
  ```

- Certifique-se de que as mensagens estejam em elementos HTML com classes como `.alert`.

---

# # ✅ PARA RODAR TODOS OS TESTES (FUNCIONAL E ACESSIBILIDADE)
- npm run test:accessibility:cadastro
- npm run test:accessibility:login
- npm run test:accessibility:conta_detalhes
- npm run test:accessibility:conta_adicionar
- npm run test:accessibility:conta_listar
- npm run test:accessibility:editar-movimentacao
- npm run test:accessibility:home
- npm run test:accessibility:movimentacao
- npm run test:accessibility:resumo

# # ✅ PARA RODAR TESTES FUNCIONAIS ESPECÍFICOS
- Login: npm run test:login
- Cadastro: npm run test:cadastro
- Detalhes da Conta: npm run test:conta_detalhes
- Adicionar Conta: npm run test:conta_adicionar
- Listar Contas: npm run test:conta_listar
- Edição de Movimentação: npm run test:editar-movimentacao
- Home: npm run test:home
- Movimentação: npm run test:movimentacao
- Resumo: npm run test:resumo

## ✅ DICA FINAL

- **Mantenha o `chromedriver.exe` sempre atualizado** conforme seu navegador.
- Testes automatizados são uma forma poderosa de garantir a **qualidade contínua** do sistema.

---

🧪 *Automatize com confiança. Garanta qualidade com velocidade!*  
💻 *ContaFácil + Selenium = 💙*
