
# 💾 Banco de Dados da Empresa de Desenvolvimento de Software

## Visão Geral

Este repositório contém o script SQL para a criação do banco de dados de uma empresa fictícia de desenvolvimento de software. O modelo de dados foi desenvolvido como parte de um trabalho de **Análise e Modelagem de Sistemas** e tem como objetivo gerenciar informações cruciais sobre:

* **Colaboradores** (funcionários) e seus **Departamentos**.
* **Clientes** e os **Projetos** que a empresa desenvolve para eles.
* **Tarefas** dentro de cada projeto.
* **Tecnologias** utilizadas nos projetos.
* **Treinamentos** oferecidos aos colaboradores.

## 🚀 Estrutura do Banco de Dados

O script cria um total de **11 tabelas**, sendo 7 tabelas principais e 4 tabelas associativas para gerenciar relacionamentos de muitos para muitos (N:M).

### Tabelas Principais

| Tabela | Descrição | Relacionamentos |
| :--- | :--- | :--- |
| `TBL_DEPARTAMENTO` | Armazena a lista de departamentos da empresa (Ex: Desenvolvimento, RH, Comercial). | **1:N** com `TBL_COLABORADOR` |
| `TBL_COLABORADOR` | Informações dos funcionários, incluindo salário, cargo e departamento. | **N:1** com `TBL_DEPARTAMENTO` |
| `TBL_CLIENTE` | Dados dos clientes (Pessoa Física ou Pessoa Jurídica). | **1:N** com `TBL_PROJETO` |
| `TBL_PROJETO` | Detalhes dos projetos em andamento, concluídos, etc. (prazo, orçamento, status). | **N:1** com `TBL_CLIENTE` |
| `TBL_TAREFA` | Tarefas específicas dentro de cada projeto, atribuídas a um colaborador. | **N:1** com `TBL_PROJETO` e `TBL_COLABORADOR` |
| `TBL_TECNOLOGIA` | Lista de tecnologias (Linguagens, Frameworks, Bancos, Ferramentas). | **N:M** com `TBL_PROJETO` |
| `TBL_TREINAMENTO` | Registra os treinamentos disponíveis para os colaboradores. | **N:M** com `TBL_COLABORADOR` |

### Tabelas Associativas (N:M)

As tabelas a seguir resolvem os relacionamentos de muitos para muitos:

| Tabela | Relacionamento | Campos Adicionais |
| :--- | :--- | :--- |
| `TBL_COLABORADOR_PROJETO` | Colaborador pode participar de vários projetos e um projeto tem vários colaboradores. | `papel_no_projeto` |
| `TBL_PROJETO_TECNOLOGIA` | Projeto usa várias tecnologias e uma tecnologia é usada em vários projetos. | |
| `TBL_COLABORADOR_TREINAMENTO` | Colaborador pode fazer vários treinamentos e um treinamento tem vários participantes. | `data_inscricao` |

## 🛠️ Como Usar o Script

### Pré-requisitos

Para executar este script, você precisará de:

1.  Um **Sistema de Gerenciamento de Banco de Dados (SGBD)** que suporte a sintaxe SQL padrão, como **MySQL**, **MariaDB** ou outro compatível com a sintaxe utilizada (incluindo `AUTO_INCREMENT` e o tipo `ENUM`).
2.  Uma ferramenta de linha de comando ou interface gráfica (ex: DBeaver, MySQL Workbench, phpMyAdmin) para executar o arquivo.

### Execução

1.  **Crie um novo banco de dados** vazio no seu SGBD (ex: `CREATE DATABASE empresa_software;`).
2.  **Selecione o banco de dados** recém-criado (ex: `USE empresa_software;`).
3.  **Execute o conteúdo do script SQL** fornecido. O script criará todas as tabelas na ordem correta, garantindo que as chaves estrangeiras (`FOREIGN KEY`) sejam estabelecidas sem erros.

```sql
-- Exemplo de execução (varia conforme o SGBD)
CREATE DATABASE empresa_software;
USE empresa_software;

-- (Cole e execute o conteúdo do script SQL aqui)# trabalho-de-modelagem-de-sistemas
