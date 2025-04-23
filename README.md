
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
- `id_produtor` (PK)
- `nome`
- `cpf`
- `email`
- `telefone`

### Talhão
- `id_talhao` (PK)
- `nome`
- `area`
- `localizacao`
- `id_produtor` (PK)

Relacionamento: **Produtor 1:N Talhão**

### Cultura
- `id_cultura` (PK)
- `nome`
- `tipo`
- `ciclo`

### Talhão_Cultura (Entidade Associativa)
- `id_talhao` (PK, FK)
- `id_cultura` (PK, FK)
- `data_plantio`
- `status`

Relacionamento: **Cultura N:N Talhão**

### Sensor Ambiental
- `id_sensor` (PK)
- `tipo_sensor` (umidade, pH, nutrientes NPK, temperatura solo, radiação solar, clima, salinidade)
- `modelo`
- `unidade_medida`
- `descricao`

### Leitura de Sensor
- `id_leitura` (PK)
- `id_sensor` (FK)
- `id_talhao` (FK)
- `data_hora`
- `valor`

### Plantação
- `id_plantacao` (PK)
- `id_produtor` (FK)
- `id_cultura` (FK)
- `localizacao`

### Ajuste
- `id_ajuste` (PK)
- `id_plantacao` (FK)
- `data_hora`
- `tipo_ajuste`
- `quantidade`


Relacionamento: **Sensor 1:N Leitura**  
Relacionamento: **Talhão 1:N Leitura**

---

## Sensores Ambientais Inclusos

1. Sensor de Umidade  
2. Sensor de pH
3. Sensor de Nutrientes (Fósforo e Potássio - NPK)
4. Sensor de Temperatura do Solo
5. Sensor Climático (Estação Metereológica Local)
6. Sensor de Radiação Solar/ Luminosidade
7. Sensor de Salinidade
---

## Observações
- Todas as entidades possuem identificador único (chave primária).
- O modelo contempla a rastreabilidade das culturas em cada talhão e o monitoramento ambiental com sensores integrados.
