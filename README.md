
# Entrega: Fase 2 - Capítulo 1
**Projeto: Sistema de Monitoramento Inteligente de Plantacao**

## Integrantes
- Mauricio Araújo - RM566040
- Igor Herson - RM563980

---

## Objetivo
Desenvolver o Modelo Entidade Relacionamento (MER) e o Diagrama Entidade Relacionamento (DER) para um sistema de agricultura digital com foco em controle de talhões, produtores, culturas e sensores ambientais, considerando relações 1:N e N:N entre entidades.

---

## Entidades e Relacionamentos

### Produtor
- `produtor_id` (PK)
- `nome`
- `cpf`
- `email`

### Talhão
- `talhao_id` (PK)
- `nome`
- `area`
- `localizacao`
- `produtor_id` (FK)

Relacionamento: **Produtor 1:N Talhão**

### Cultura
- `cultura_id` (PK)
- `nome`
- `tipo`
- `ciclo`

### Talhão_Cultura (Entidade Associativa)
- `talhao_id` (PK, FK)
- `cultura_id` (PK, FK)
- `data_plantio`
- `status`

Relacionamento: **Cultura N:N Talhão**

### Sensor Ambiental
- `sensor_id` (PK)
- `tipo` (temperatura solo, radiação solar, clima, salinidade)
- `unidade_medida`
- `descricao`

### Leitura de Sensor
- `leitura_id` (PK)
- `sensor_id` (FK)
- `talhao_id` (FK)
- `valor`
- `data_hora`

Relacionamento: **Sensor 1:N Leitura**  
Relacionamento: **Talhão 1:N Leitura**

---

## Sensores Ambientais Inclusos

1. Sensor de Temperatura do Solo  
2. Sensor Climático (Estação Meteorológica Local)  
3. Sensor de Radiação Solar / Luminosidade  
4. Sensor de Salinidade  

---

## Observações
- Todas as entidades possuem identificador único (chave primária).
- O modelo contempla a rastreabilidade das culturas em cada talhão e o monitoramento ambiental com sensores integrados.
