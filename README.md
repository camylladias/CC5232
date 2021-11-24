# Projeto Disciplina CC5232 Banco de Dados - FEI 

*O trabalho prático tem por objetivo desenvolver um projeto de Banco de Dados que simula uma clínica veterinária. Todos os dados das tabelas são fictícios.*
🐱 🐹 🐶 🦎

**Integrantes:** Camylla Dias e Marcella Costa


![ipetcare-logo](https://user-images.githubusercontent.com/37374749/143184679-b9bb6239-903d-4f62-bb11-b6d2799959e0.JPG)
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
*Fisioterapia:* Recuperação física do pet pós cirurgia, pós trauma etc.<br>

