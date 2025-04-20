# Projeto: Sistema de Monitoramento Inteligente de Plantacao
**Responsavel:** Mauricio Araujo/ Igor Herson
**RM:** 566040/ 
**Fase:** 2
**Capitulo:** 1

---

## 🌾 Descricao do Projeto

Este projeto simula um sistema de monitoramento agricola inteligente para a **FarmTech Solutions**, voltado à coleta e analise de dados em plantacoes atraves de sensores. A solucao busca armazenar os dados dos sensores e aplicar ajustes automatizados de irrigacao e aplicacao de nutrientes, com base nas leituras recebidas.

---

## 🎯 Objetivo

Modelar o **MER (Modelo Entidade-Relacionamento)** de um banco de dados relacional capaz de:

- Armazenar leituras de sensores em tempo real;
- Controlar plantacoes, culturas, produtores e ajustes realizados;
- Suportar sensores modernos utilizados na agricultura de precisao.

---

## 🧱 Entidades e Atributos

### 🔹 Sensor

Armazena os tipos de sensores utilizados no campo.

| Atributo         | Tipo     | Descricao                                        |
| ---------------- | -------- | ------------------------------------------------ |
| `id_sensor`      | int (PK) | Identificador do sensor                          |
| `tipo_sensor`    | varchar  | Tipo: umidade, pH, nutrientes, temperatura_solo |
| `modelo`         | varchar  | Modelo do sensor                                 |
| `unidade_medida` | varchar  | Unidade utilizada (%, pH, mg/kg, °C, etc.)       |

### 🔹 Leitura

Armazena as leituras geradas por cada sensor.

| Atributo     | Tipo     | Descricao                       |
| ------------ | -------- | ------------------------------- |
| `id_leitura` | int (PK) | Identificador da leitura        |
| `id_sensor`  | int (FK) | Sensor responsavel pela medicao |
| `data_hora`  | datetime | Data e hora da leitura          |
| `valor`      | double   | Valor da medicao registrada     |

### 🔹 Cultura

Define o tipo de cultivo realizado.

| Atributo     | Tipo     | Descricao                              |
| ------------ | -------- | -------------------------------------- |
| `id_cultura` | int (PK) | Identificador da cultura               |
| `nome`       | varchar  | Nome da cultura (ex: soja, cafe)       |
| `tipo`       | varchar  | Tipo: leguminosa, cereal, tuberculo... |

### 🔹 Produtor

Armazena os dados do responsavel pela plantacao.

| Atributo      | Tipo     | Descricao                 |
| ------------- | -------- | ------------------------- |
| `id_produtor` | int (PK) | Identificador do produtor |
| `nome`        | varchar  | Nome do produtor          |
| `email`       | varchar  | E-mail                    |
| `telefone`    | varchar  | Contato telefonico        |

### 🔹 Plantacao

Representa uma area cultivada.

| Atributo       | Tipo     | Descricao                        |
| -------------- | -------- | -------------------------------- |
| `id_plantacao` | int (PK) | Identificador da plantacao       |
| `id_produtor`  | int (FK) | Dono da plantacao                |
| `id_cultura`   | int (FK) | Tipo de cultura cultivada        |
| `localizacao`  | varchar  | Ponto geografico ou nome da area |

### 🔹 Ajuste

Representa acoes realizadas com base nos dados dos sensores.

| Atributo       | Tipo     | Descricao                                 |
| -------------- | -------- | ----------------------------------------- |
| `id_ajuste`    | int (PK) | Identificador do ajuste                   |
| `id_plantacao` | int (FK) | Plantacao onde foi feito o ajuste         |
| `data_hora`    | datetime | Momento em que o ajuste foi realizado     |
| `tipo_ajuste`  | varchar  | Tipo: aplicacao de agua, nutrientes, etc. |
| `quantidade`   | double   | Quantidade aplicada (litros, kg...)       |

---

## 🔗 Relacionamentos

| Entidade A | Entidade B | Tipo   | Observacao                                  |
| ---------- | ---------- | ------ | ------------------------------------------- |
| Sensor     | Leitura    | 1:N    | Um sensor gera muitas leituras              |
| Produtor   | Plantacao  | 1:N    | Um produtor pode ter varias plantacoes      |
| Cultura    | Plantacao  | 1:N    | Uma cultura pode estar em varias plantacoes |
| Plantacao  | Ajuste     | 1:N    | Uma plantacao recebe diversos ajustes       |
| Sensor     | Plantacao  | N:N*   | Opcional, caso sensores sejam fixos         |

---

## 🧐 Destaque tecnico: Sensor adicional moderno

Incluimos no modelo um **sensor de temperatura do solo**, pratica moderna na agricultura de precisao, que permite prever melhor a absorcao de nutrientes e a necessidade de irrigacao. Isso traz valor estrategico e aumenta o realismo da modelagem proposta.

---

## 📎 Arquivos do repositório

- `modelo.dmd` → Modelo criado no SQL Developer Data Modeler
- `diagrama.png` → Imagem do DER para visualizacao rapida
- `README.md` → Este documento explicativo

---

## 📜 Licenca

Uso academico, sob orientacao da FIAP.
