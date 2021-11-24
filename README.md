# Projeto Disciplina CC5232 Banco de Dados - FEI 

*O trabalho prático tem por objetivo desenvolver um projeto de Banco de Dados que simula uma clínica veterinária.<br> O projeto foi criado utilizando PostgreSQL 14, pgAdmin 4 e ElephantSQL (GCP). Todos os dados das tabelas são fictícios.* 🐱 🐹 🐶 🦎

**Integrantes:** Camylla Dias e Marcella Costa
<br><br>
### Tópicos
[1. Universo do Discurso](#universo-do-discurso)<br>
[2. ER Diagram](#er-diagram)<br>
[3. Modelo Relacional](#modelo-relacional)<br>
[4. Principais Atividades](#principais-atividades)<br>
[5. Entidades e seus Atributos](#entidades-e-seus-atributos)<br>
[6. Comandos](#comandos)<br>
[7. Consulta Solicitada](#consulta-solicitada)


---

### Universo do Discurso
Objetivo: O objetivo do sistema é gerenciar uma clínica veterinária onde é possível
realizar o cadastro de dados dos clientes, funcionários da clínica e o agendamento de
consultas.<br><br>
Funcionalidades: O sistema possui as funcionalidades de cadastrar novos clientes
e funcionários, informar dados dos funcionários, informar os dados do tutor, quantidade de
animais de estimação que o tutor possui, dados sobre o animal de estimação, histórico de
consultas, agendamento de consulta, alterar data de consulta, cancelar consulta.<br><br><br><br>

### ER Diagram:
![MER-ProjetoBD drawio](https://user-images.githubusercontent.com/37374749/143149924-49ff06f5-9514-438e-8c90-848f06809072.png)
---
### Modelo Relacional:
![ERDDiagram1](https://user-images.githubusercontent.com/37374749/143148632-426de5d1-eb23-45e3-a1e8-f05de9dd758c.jpg)
---
<br><br>
### Principais atividades:
1: Contratação de funcionários especializados para cuidar dos animais<br>
2: Atendimento especializado para animais.
<br><br><br>

### Entidades e seus Atributos:
- **Pessoa:** Representa as contas cadastradas no sistema, está dividido entre Tutor e Funcionário. Uma pessoa pode ser tanto funcionário quanto tutor de um pet.
*Nome:* Autoexplicativo.<br>
*CPF:* Autoexplicativo.<br>
*Data de Nascimento:* Autoexplicativo.<br><br>

- **Tutor:** Pessoas donas de animais de estimação, responsáveis por realizar as solicitações de consultas. Herda todos os atributos de Pessoa.<br>
*ID_Tutor:* ID gerado assim que o tutor é cadastrado no sistema.<br><br>

- **Pet:** Animais de estimação dos tutores.<br>
*Nome:* Autoexplicativo.<br>
*Espécie:* Autoexplicativo.<br>
*Idade:* Autoexplicativo.<br>
*Gênero:* Autoexplicativo.<br>
*ID Carteira de Vacinação:* Número da carteirinha de vacinação do Pet.<br><br>

- **Funcionário:** Pessoas que prestam serviços estão divididas entre Veterinário(a), Técnico Veterinário(a) e Recepcionista.<br>
*Salário:* Autoexplicativo.<br>
*Benefícios:* Benefícios que a empresa disponibiliza para o funcionário como VT, VR e convênio.<br>
*ID_Funcionário:* ID gerado assim que o funcionário é cadastrado no sistema.<br><br>

- **Veterinário:** Funcionário da clínica, o profissional possui formação em medicina veterinária e com especialização em felinos e roedores, por
exemplo. Herda os atributos de Funcionário e Pessoa.<br>
*CRMV:* Registro obrigatório para atuar como médico veterinário.<br>
*Formação:* Formação em Medicina Veterinária e Especialização.<br><br>

- **Técnico Veterinário:** Funcionário da clínica, o profissional possui formação em técnico de veterinária e auxilia em atividades
da consulta. Herda os atributos de Funcionário e Pessoa.<br>
*Curso_Técnico:* Formação de Técnico Veterinário.<br><br>

- **Recepcionista:** Profissional responsável por recepcionar tutores e pets na clínica veterinária, também deve administrar a agenda de consultas. Herda os atributos de
Funcionário e Pessoa.<br><br>

- **Consulta:** Representa os dados necessários para registrar uma consulta no sistema. Herda também os atributos: ID_Veterinário, ID_Tutor, ID_Pet, ID_Tipo_Consulta.<br>
*ID_Consulta:* Identificação única da consulta.<br>
*Valor:* Custo da consulta na clínica.<br>
*Data:* Autoexplicativo.<br>
*Horário:* Autoexplicativo<br>
*Tipo_Consulta:* Representa os procedimentos disponíveis para realização na clínica veterinária.<br>
*ID_Tipo_Consulta:* Identificação única do procedimento a ser realizado.<br>
*Clínica_Geral:* Atendimento para verificar a saúde geral do pet.<br>
*Castração:* Castração de animais de ambos os sexos.<br>
*Higienização:* Banho e Tosa.<br>
*Dentista:* Limpeza, extração ou qualquer outro procedimento relacionado.<br>
*Fisioterapia:* Recuperação física do pet pós cirurgia, pós trauma etc.
<br><br><br>

### Comandos
*obs: a base de dados foi criada atráves da utilização do ElephantSQL.*
- Cria tabela Pessoa
```
CREATE TABLE Pessoa (
cpf BIGINT PRIMARY KEY,
nome VARCHAR(255),
email VARCHAR(255) UNIQUE,
data_nascimento DATE
);
```
<br><br>
- Cria tabela Funcionário
```
CREATE TABLE Funcionario (
id_funcionario INT PRIMARY KEY,
cpf BIGINT,
FOREIGN KEY (cpf) REFERENCES Pessoa (cpf),
salario DECIMAL(16,2),
vale_refeicao VARCHAR(255),
vale_transporte VARCHAR(255),
convenio_medico VARCHAR(255));
```
<br><br>
- Cria tabela Tutor
```
CREATE TABLE Tutor (
id_cliente INT PRIMARY KEY,
cpf BIGINT,
FOREIGN KEY (cpf) REFERENCES Pessoa (cpf)
);
```
<br><br>
- Adiciona Foreign Key:
```
ALTER TABLE Tutor ADD FOREIGN KEY (id_pet) REFERENCES 
Pet (id_pet)
```
*obs: adicionar foreign key após a criação da tabela de referência.*
<br><br>
- Cria tabela Pet
```
CREATE TABLE Pet (
id_pet INT PRIMARY KEY,
id_carteira_vacinacao BIGINT UNIQUE,
id_cliente INT,
FOREIGN KEY (id_cliente) REFERENCES Tutor (id_cliente),
nome_pet VARCHAR(255),
especie VARCHAR(255),
data_nascimento_pet DATE,
genero VARCHAR(10)
);
```
<br><br>
- Cria tabela Veterinário
```
CREATE TABLE Veterinario (
id_funcionario INT UNIQUE,
FOREIGN KEY (id_funcionario) REFERENCES Funcionario (id_funcionario),
crmv BIGINT UNIQUE,
curso_graduacao VARCHAR(255),
curso_especializacao VARCHAR(255)
);
```
<br><br>
- Cria tabela Técnico Veterinário
```
CREATE TABLE Tecnico_Veterinario (
id_funcionario INT UNIQUE,
FOREIGN KEY (id_funcionario) REFERENCES Funcionario (id_funcionario),
curso_tecnico VARCHAR(255)
);
```
<br><br>
- Cria tabela Recepcionista
```
CREATE TABLE Recepcionista (
id_funcionario INT UNIQUE,
FOREIGN KEY (id_funcionario) REFERENCES Funcionario (id_funcionario)
);
```
<br><br>
- Cria tabela Consulta
```
CREATE TABLE Consulta (
id_consulta INT PRIMARY KEY,
id_tipo_consulta INT,
id_funcionario INT,
id_cliente INT,
id_pet INT,
valor DECIMAL(16,2),
data_consulta DATE,
horario TIME,
FOREIGN KEY (id_funcionario) REFERENCES Veterinario (id_funcionario),
FOREIGN KEY (id_cliente) REFERENCES Tutor (id_cliente),
FOREIGN KEY (id_pet) REFERENCES Pet (id_pet)
);
```
<br><br>
- Adiciona Foreign Key
```
ALTER TABLE Consulta ADD FOREIGN KEY (id_tipo_consulta) REFERENCES
Tipo_Consulta (id_tipo_consulta)
```
<br><br>
- Cria tabela Tipo Consulta
```
CREATE TABLE Tipo_Consulta (
id_tipo_consulta INT PRIMARY KEY,
clinica_geral BOOLEAN,
castracao BOOLEAN,
higienizacao BOOLEAN,
dentista BOOLEAN,
fisioterapia BOOLEAN
);
```
<br><br><br>
### Consulta Solicitada:
*"Liste as consultas durante o primeiro semestre de 2021? Agrupe a informação por espécie de animal tratado e mês."*
- Query Utilizada:
```
SELECT nome_pet, especie, Data_Consulta
FROM Consulta as Cons inner join
Pet as Pet on Pet.id_pet = Cons.id_pet
WHERE Data_Consulta BETWEEN '01-01-2021' AND '06-30-2021'
GROUP BY especie, Data_Consulta, nome_pet
ORDER BY Data_Consulta
```
<br><br><br>
 O arquivo desta base de dados se encontra neste repositório. 🤙<br><br>
![ipetcare-logo](https://user-images.githubusercontent.com/37374749/143184679-b9bb6239-903d-4f62-bb11-b6d2799959e0.JPG)
<br><br>
[Subir ⬆️](#projeto-disciplina-cc5232-banco-de-dados---fei)
