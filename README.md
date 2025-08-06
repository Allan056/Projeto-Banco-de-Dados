[Projeto - Criação de Empresa.docx](https://github.com/user-attachments/files/21608506/Projeto.-.Criacao.de.Empresa.docx)# 📊 Projeto de Banco de Dados
Este projeto tem como objetivo o desenvolvimento de um banco de dados relacional completo, passando por todas as etapas essenciais: da concepção do negócio à implementação prática em SQL Server. A proposta foi desenvolvida com base em uma empresa fictícia criada especialmente para esse fim, com foco em aplicar técnicas modernas de modelagem e consulta de dados.

---

## 🧱 Estrutura do Projeto

### 🔹 Fase 1 – Criação da Empresa Fictícia

Nesta primeira etapa, utilizei **Inteligência Artificial** para construir a identidade da empresa:

- Nome da empresa
- Logotipo
- Descrição do negócio
- Público-alvo
- Produtos ou serviços oferecidos

Essas informações serviram como base para a estrutura de dados nas fases seguintes.

[Projeto - Criação de Empresa.docx](https://github.com/user-attachments/files/21608508/Projeto.-.Criacao.de.Empresa.docx)

[NutriBaby_ Alimentação Saudável e Prática para Crianças e Bebês.pptx](https://github.com/user-attachments/files/21608519/NutriBaby_.Alimentacao.Saudavel.e.Pratica.para.Criancas.e.Bebes.pptx)

---

### 🔹 Fase 2 – Modelagem de Dados

#### ✅ Parte 1: Modelagem Conceitual

Criação do **Diagrama Entidade-Relacionamento (DER)** com foco em:

- Entidades e atributos principais
- Relacionamentos entre entidades
- Aplicação das regras de **normalização até a 3ª Forma Normal (3FN)**
<img width="2977" height="2562" alt="NutriBaby - Conceitual -" src="https://github.com/user-attachments/assets/70604cc2-bc39-4af7-a70f-6b7084d6e285" />




#### ✅ Parte 2: Modelagem Lógica

Conversão do modelo conceitual para o **modelo lógico**, definindo:

- Tabelas e colunas
- Tipos de dados apropriados
- Chaves primárias e estrangeiras
- Restrições de integridade
<img width="2873" height="1414" alt="02-NutriBaby - M_logico_r" src="https://github.com/user-attachments/assets/1db92925-a56b-4816-b438-9fab3917b72f" />



#### ✅ Parte 3: Implementação no SQL Server

- Criação do banco no **SQL Server**
- Implementação das tabelas e relacionamentos
- Aplicação de restrições (PK, FK, índices)

---

## 🔍 Consultas SQL com Situações-Problema

Foram desenvolvidas **consultas SQL** envolvendo múltiplas tabelas com **JOINs** para resolver cenários práticos do negócio. Essas consultas demonstram o uso de:

- `INNER JOIN`, `LEFT JOIN`
- Filtros e condições (`WHERE`, `AND`, `OR`)
- Ordenações e agrupamentos (`ORDER BY`, `GROUP BY`)
- Cenários reais de busca e análise de dados

---

## 🛠️ Tecnologias Utilizadas

- **SQL Server**
- **Modelagem relacional (DER, Modelo Lógico)**
- **Ferramentas de diagramação (ex: Draw.io, DBDesigner)**
- **Linguagem SQL (DDL & DML)**
[Uploading ATIVADEFINAL.sql…]()

## 🗄️ Script do Banco de Dados

Este repositório inclui o script completo de criação, inserção e consulta do banco de dados NutriBaby.

📄 [`script_banco_nutribaby.sql`](scripts_sql/script_banco_nutribaby.sql)


✅ Aprendizados
Este projeto consolidou conhecimentos sobre:

Modelagem de dados desde o nível conceitual até a implementação

Normalização de dados para garantir integridade

Criação de relacionamentos sólidos entre entidades

Escrita de consultas SQL eficientes para resolver problemas reais

📌 Status do Projeto
✅ Concluído
📌 Aberto para melhorias futuras e integração com aplicações front-end

