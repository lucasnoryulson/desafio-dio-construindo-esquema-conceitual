# **Modelo de Oficina Mecânica - Bootcamp Suzano**

Este projeto apresenta o esquema conceitual e relacional para um sistema de **controle e gerenciamento de ordens de serviço** em uma oficina mecânica. O objetivo foi criar um modelo que represente as entidades principais, seus atributos e os relacionamentos necessários para organizar as operações da oficina.

---

## **Descrição do Modelo**

### **Entidades e Atributos**

1. **Cliente**
   - `idCliente` (INT, PK): Identificador único do cliente.
   - `Nome` (VARCHAR(45)): Nome do cliente.
   - `Telefone` (VARCHAR(15)): Telefone do cliente.
   - `Endereço` (VARCHAR(100)): Endereço do cliente.

2. **Veículo**
   - `idVeículo` (INT, PK): Identificador único do veículo.
   - `Modelo` (VARCHAR(45)): Modelo do veículo.
   - `Placa` (VARCHAR(45)): Placa do veículo.
   - `Ano` (INT): Ano de fabricação do veículo.

3. **Mecânico**
   - `idMecânico` (INT, PK): Identificador único do mecânico.
   - `Nome` (VARCHAR(45)): Nome do mecânico.
   - `CPF` (INT): Cadastro de Pessoa Física.
   - `Especialidade` (VARCHAR(45)): Área de especialização do mecânico (e.g., motor, suspensão).

4. **Ordem de Serviço (OS)**
   - `idOrdem de Serviço` (INT, PK): Identificador único da ordem de serviço.
   - `Data de início` (DATETIME): Data em que a OS foi emitida.
   - `Data de entrega` (DATETIME): Data prevista para a conclusão.
   - `Tipo de serviço` (VARCHAR(45)): Tipo de serviço realizado (e.g., revisão, conserto).
   - `Detalhes do serviço` (VARCHAR(255)): Descrição detalhada dos serviços.
   - `Valor total` (DOUBLE): Valor total da OS, incluindo mão de obra e peças.
   - `Veículo_idVeículo` (INT, FK): Relacionamento com o veículo associado à OS.

5. **Peça**
   - `idPeça` (INT, PK): Identificador único da peça.
   - `Nome` (VARCHAR(45)): Nome da peça.
   - `Valor` (DOUBLE): Valor unitário da peça.

6. **Peças Utilizadas**
   - Relaciona as peças usadas em cada ordem de serviço.
   - Atributos:
     - `Ordem de Serviço_idOrdem` (INT, FK): Ordem de Serviço associada.
     - `Peça_idPeça` (INT, FK): Peça utilizada.
     - `Quantidade` (INT): Quantidade de peças utilizadas.
     - `Valor Total` (DOUBLE): Valor total com base na quantidade.

7. **Equipe**
   - Representa a relação entre os mecânicos e as ordens de serviço.
   - Atributos:
     - `Mecânico_idMecânico` (INT, FK): Mecânico associado à ordem de serviço.
     - `Ordem de Serviço_idOrdem` (INT, FK): Ordem de Serviço associada.

---

### **Relacionamentos**

1. **Cliente - Veículo**
   - Um cliente pode possuir vários veículos (**1:N**).

2. **Veículo - Ordem de Serviço**
   - Um veículo pode ter várias ordens de serviço associadas (**1:N**).

3. **Ordem de Serviço - Peças Utilizadas**
   - Uma ordem de serviço pode usar várias peças, e uma peça pode ser usada em várias ordens (**N:N**).

4. **Ordem de Serviço - Mecânicos (Equipe)**
   - Cada ordem de serviço pode ser atribuída a uma equipe de mecânicos (**N:N**).

---

## **Destaques do Modelo**

- **Organização Clara**: Cada entidade representa um aspecto importante do gerenciamento da oficina.
- **Relacionamentos Detalhados**: A implementação de relacionamentos permite rastrear as peças usadas, os mecânicos atribuídos e os serviços realizados.
- **Flexibilidade**: Suporte para múltiplas peças por OS e múltiplos mecânicos por equipe.

---

## **Como Reproduzir**

1. **Ferramentas Necessárias**: 
   - MySQL Workbench, DBDesigner ou qualquer outro software de modelagem de banco de dados.

2. **Passos**:
   - Baixe o arquivo do modelo conceitual no repositório.
   - Abra o arquivo na ferramenta de modelagem.
   - Verifique as entidades, atributos e relacionamentos no diagrama.

---

## **Possíveis Melhorias**

1. **Histórico de Revisões**:
   - Implementar uma tabela para manter um histórico detalhado de revisões realizadas em cada veículo.

2. **Status da Ordem de Serviço**:
   - Expandir o campo de status para usar uma tabela dedicada com opções como "Pendente", "Em Execução", "Concluída", etc.

3. **Tabela de Mão-de-Obra**:
   - Adicionar uma tabela para armazenar os tipos de serviços e seus valores base, facilitando o cálculo automático do valor da OS.

---

## **Sobre o Autor**

Este modelo foi desenvolvido como parte do Bootcamp **Suzano - Análise de Dados com Power BI**, com o objetivo de demonstrar habilidades em modelagem de banco de dados. O projeto está disponível para consulta em meu portfólio e é um exemplo prático de design relacional aplicado.

---

### **Licença**
Este projeto é destinado ao uso educacional e está disponível para referência em projetos similares.

---
