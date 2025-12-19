# **Chatbot com SQLite, LangChain e Hugging Face**

## **1\. Introdução**

Este projeto implementa um chatbot capaz de interpretar perguntas em linguagem natural, acessar informações em um banco de dados SQLite e devolver respostas de forma clara e amigável.

A aplicação combina o poder dos Modelos de Linguagem da Hugging Face com a orquestração do LangChain, permitindo traduzir perguntas do usuário em consultas SQL e apresentar os resultados em português natural.

## **2\. Problema Resolvido**

A implementação do projeto possibilita permitir consultas a um banco de dados SQLite, traduzir automaticamente as perguntas para a linguagem SQL e reformular as respostas em linguagem natural, tornando a experiência do usuário mais amigável.

## **3\. Modo de Resolução do Problema**

1. **Banco de Dados (SQLite)**

   * Criação do banco example.db com a tabela clientes (campos: id, nome, email, cidade).

   * Inserção de registros fictícios: *Ana Silva*, *Bruno Souza* e *Carla Mendes*.

2. **Autenticação no Hugging Face**

   * Utilização de um token de acesso (HF\_TOKEN) para baixar e rodar modelos pré-treinados.

3. **Carregamento do Modelo**

   * Uso do modelo Mistral-7B-Instruct via Hugging Face.

   * Otimizações de memória: quantização em 4 bits e offload automático CPU/GPU.

   * Criação de um pipeline de text-generation configurado para respostas curtas, determinísticas e consistentes.

4. **Integração com LangChain**

   * Conexão entre o modelo de linguagem e o banco SQLite.

   * Construção de um SQLDatabaseChain que permite converter perguntas em português em consultas SQL.

5. **Função de Perguntas**

   * Implementação da função perguntar(), que:

     * Executa a consulta no banco.

     * Formata o resultado bruto.

     * Pede ao modelo para reformular a resposta em português natural.

6. **Loop Interativo**

   * Interface no terminal, permitindo ao usuário digitar perguntas livremente.

   * O chatbot responde de forma natural, e o comando sair encerra a conversa.

## **4\. Estrutura do Projeto**

├── example.db                           \# Banco SQLite com a tabela clientes  
├── chatbot\_sqlite\_langchain.ipynb       \# Notebook principal com o código  
└── README.md                            \# Documentação do projeto

## **5\. Tecnologias Utilizadas**

* **Python 3**

* **SQLite3** → banco de dados relacional leve.

* **Pandas** → manipulação e visualização dos dados.

* **Hugging Face Transformers** → modelos de linguagem (Mistral-7B-Instruct).

* **LangChain** → integração entre LLMs e banco de dados.

* **Bitsandbytes** → quantização e otimização do modelo.

* **Accelerate** → execução em diferentes hardwares (CPU/GPU).

## **6\. Exemplos de Uso**

**Pergunta do usuário:**

🧑 Você: Quais clientes moram em São Paulo?

**Consulta SQL gerada pelo LangChain:**

SELECT \* FROM clientes WHERE cidade \= 'São Paulo';

**Resposta final do chatbot:**

🤖 Bot: Os clientes que moram em São Paulo são: Ana Silva.

Outro exemplo:

🧑 Você: Qual é o e-mail da Carla Mendes?  
🤖 Bot: O e-mail de Carla Mendes é carla@email.com.

## **7\. Resultados Obtidos**

O chatbot foi capaz de interpretar perguntas em português e gerar corretamente as consultas SQL correspondentes. As respostas foram apresentadas em linguagem natural, proporcionando uma experiência fluida e intuitiva. Além disso, a arquitetura mostrou-se eficiente mesmo em hardware limitado, devido ao uso da quantização do modelo.

## **8\. Próximos Passos**

* Adicionar interface gráfica com **Streamlit** ou **Gradio**.

* Expandir o banco de dados para cenários mais complexos.

* Testar outros modelos de linguagem (LLaMA 2, Falcon, etc.).

* Implementar autenticação e controle de acesso para consultas mais sensíveis.

* Habilitar logging de conversas para análise posterior.

