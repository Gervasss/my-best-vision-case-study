# 🚀 Caso de Estudo: Projeto My Best Vision

Este repositório contém a documentação técnica e o estudo de caso detalhado do projeto **My Best Vision**. 

Este documento descreve minha atuação, os desafios superados e as soluções de engenharia aplicadas. Por razões de confidencialidade e propriedade intelectual, o código-fonte original é privado.

---

## 📝 Visão Geral do Projeto

O **My Best Vision** é uma plataforma web desenvolvida para auxiliar clientes na escolha da lente oftálmica mais adequada às suas necessidades visuais específicas. 

A solução combina a prescrição médica com as respostas fornecidas pelo usuário em questionários estruturados sobre hábitos visuais, rotina diária e exposição a telas. Ao final, o sistema direciona o cliente para a lente que melhor atende ao seu perfil, tornando o processo de decisão assertivo e personalizado.

### Arquitetura e Ambientes
O sistema é composto por dois ambientes principais:
1.  **Ambiente do Consultor/Vendedor:** Ferramenta de apoio à venda utilizada junto ao cliente para preenchimento de dados e condução técnica.
2.  **Painel Administrativo:** Responsável pelo gerenciamento completo, incluindo controle de acesso, cadastro de lentes, definição de índices de refração e atualização de preços.

## 🛠️ Tecnologias Utilizadas

* **Frontend:** React com TypeScript (garantindo tipagem estática e segurança).
* **Estilização:** CSS.
* **Backend & Database:** Firebase (Banco de dados NoSQL e autenticação).
* **Processamento de Dados:** Biblioteca `xlsx` e API `FileReader` do navegador.

---

## 💡 Atuação e Responsabilidades

Minha atuação envolveu manutenção evolutiva, correção de falhas e o desenvolvimento de funcionalidades estratégicas:

### Correções e UX
Realizei ajustes na associação de tecnologias às lentes e implementei a exibição de vídeos explicativos, permitindo que o cliente compreendesse as escolhas técnicas no momento da compra.

### O Desafio da Automação (Destaque Técnico)
**Problema:** A atualização de preços de mais de 1.000 lentes era manual e levava semanas.
**Solução:** Desenvolvi uma funcionalidade que permite o upload de uma planilha Excel (Código da Lente vs. Novo Valor). 
**Funcionamento:** O sistema intercepta o envio, utiliza a API `FileReader` e a biblioteca `xlsx` para converter os dados em objetos JavaScript. O sistema percorre as linhas e aciona funções assíncronas para atualizar o Firebase individualmente, fornecendo feedback visual de sucesso ou erro para cada item.

**Resultado:** O tempo de processamento caiu de **semanas para menos de 2 minutos**.

---

## 💡 Funcionamento  Técnico da Atualização

Ao enviar o arquivo, o sistema intercepta o envio do formulário, evitando o recarregamento da página e mantendo o processamento totalmente controlado dentro da aplicação. Caso nenhum arquivo seja selecionado, o sistema exibe mensagens de erro claras e temporárias, orientando o administrador sobre a ação necessária.
Quando um arquivo válido é fornecido, o sistema entra em estado de carregamento e utiliza a API FileReader do navegador para ler o conteúdo do arquivo local. Os dados são então interpretados como uma planilha Excel por meio da biblioteca xlsx, que converte a primeira aba do arquivo em uma estrutura de objetos JavaScript.
Cada linha da planilha representa uma lente, contendo seu código e o novo preço. O sistema percorre essas linhas uma a uma, buscando cada lente correspondente dentro da coleção de lentes previamente recuperada do banco de dados do Firebase. Quando a lente é encontrada, a função responsável pela edição é acionada, atualizando o preço no banco de dados de forma segura e consistente.
Caso alguma lente presente na planilha não exista no banco de dados, o sistema registra esse evento e informa ao administrador, garantindo transparência e facilitando a correção de inconsistências. Erros pontuais durante a atualização de uma lente não interrompem o processo como um todo, permitindo que as demais atualizações continuem normalmente.
Ao final do processamento, o sistema apresenta um feedback visual indicando quais lentes foram atualizadas com sucesso, além de mensagens de confirmação ou erro quando necessário. Independentemente do resultado, o estado de carregamento é finalizado, sinalizando o encerramento da operação.




## ⚙️ Como Rodar o Projeto (Ambiente de Desenvolvimento)

Embora o código seja privado, abaixo descrevo as etapas necessárias para configurar e rodar uma aplicação com esta arquitetura (React + Firebase):

### 1. Pré-requisitos
* Node.js (v18+)
* Uma conta no [Firebase Console](https://console.firebase.google.com/)

### 2. Configuração do Firebase
Crie um projeto no Firebase e obtenha suas credenciais. No diretório raiz, crie um arquivo `.env` com as seguintes chaves:
```env
REACT_APP_FIREBASE_API_KEY="sua_api_key"
REACT_APP_FIREBASE_AUTH_DOMAIN="seu_projeto.firebaseapp.com"
REACT_APP_FIREBASE_PROJECT_ID="seu_projeto_id"
REACT_APP_FIREBASE_STORAGE_BUCKET="seu_projeto.appspot.com"
REACT_APP_FIREBASE_MESSAGING_SENDER_ID="seu_sender_id"
REACT_APP_FIREBASE_APP_ID="seu_app_id"



```

### 3. Instalação e Execução

No terminal, execute os comandos abaixo:

```bash
# Instalar as dependências (incluindo React, TypeScript, Firebase e XLSX)
npm install

# Iniciar o servidor de desenvolvimento
npm start

```

### 4. Simulação da Automação de Preços

Para testar a funcionalidade que desenvolvi:

1. Acesse o Painel Administrativo.
2. Prepare um arquivo `.xlsx` com as colunas `codigo` e `preco`.
3. Realize o upload no módulo de "Atualização de Preços".
4. Acompanhe o log de processamento e a atualização em tempo real no Firestore.

---

## 📈 Impacto Operacional

A automatização consolidou-se como um elemento estratégico para a eficiência do Grupo Mercadótica, garantindo que o catálogo de produtos esteja sempre atualizado diante de reajustes frequentes, com zero erro humano.



**Desenvolvido por Gervásio Cardoso** [LinkedIn](https://www.google.com/search?q=https://www.linkedin.com/in/gerv%C3%A1sio-cardoso/) | [GitHub](https://www.google.com/search?q=https://github.com/Gervasss)

---
## 📸 Demonstração e Resultados

Abas apresentadas ao cliente :

<img width="886" height="417" alt="image" src="https://github.com/user-attachments/assets/b2ee16ee-526e-4f78-aa3c-ec01e9931f72" />
<img width="886" height="419" alt="image" src="https://github.com/user-attachments/assets/21fdf014-fac5-4d8a-a4cc-6c0bb9afd534" />
<img width="886" height="418" alt="image" src="https://github.com/user-attachments/assets/a79ebd27-6d71-41b4-9875-71cddde86fe1" />

Ambiente do Admin :

<img width="886" height="421" alt="image" src="https://github.com/user-attachments/assets/05516f09-a83b-4550-b040-22894b1ce6d9" />
<img width="886" height="422" alt="image" src="https://github.com/user-attachments/assets/cabf0ced-4c88-4d50-9c57-71b8fa36da28" />

Planilha criada para puxar os dados das lentes :

<img width="886" height="359" alt="image" src="https://github.com/user-attachments/assets/306ce2d0-38af-43dd-80e4-e954f96740e1" />

Tela onde é feito a atualização dos valores :

<img width="886" height="421" alt="image" src="https://github.com/user-attachments/assets/682bec10-667d-4185-8849-568bab20cacb" />



---
