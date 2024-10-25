# Projeto: Processamento de Dados Simplificado com Power BI e MySQL no Azure
Descrição do Projeto  
Este projeto é uma aplicação prática de processamento e transformação de dados usando Power BI e MySQL. O objetivo é criar e configurar um banco de dados em uma instância MySQL no Azure, integrar com o Power BI e realizar transformações e análises dos dados, preparando-os para um modelo estrela.

# Objetivos  
Configurar uma instância MySQL no Azure.  
Criar e popular o banco de dados com os scripts SQL fornecidos.  
Realizar transformações e validações de dados no Power BI para análise.  
Tecnologias Utilizadas  
Microsoft Azure: Instância MySQL hospedada para o banco de dados.  
MySQL Workbench: Ferramenta para gerenciar e manipular o banco de dados.  
Power BI: Ferramenta de BI usada para integrar, transformar e visualizar os dados.  
Passo a Passo do Projeto  
# 1. Configuração da Instância MySQL no Azure  
Passo: Criar uma instância MySQL no portal Azure.  
Detalhes: Definir nome, usuário, senha e demais configurações. Obter as credenciais de conexão para uso no MySQL Workbench e Power BI.  
# 2. Criação e População do Banco de Dados  
Script: script_bd_company.sql  
Descrição: Este script cria as tabelas employee e departament com suas chaves primárias e estrangeiras, e restrições.  
Script: insercao_de_dados_e_queries_sql.sql  
Descrição: Este script insere dados de exemplo na tabela employee.  
# 3. Integração com o Power BI  
Conectar o Power BI ao banco de dados MySQL no Azure usando as credenciais da instância.  
Carregar os dados das tabelas employee e departament para o Power BI para iniciar as transformações de dados.  
# 4. Transformações de Dados no Power BI  
Verificação de Cabeçalhos e Tipos de Dados: Certificar que cabeçalhos e tipos estão corretos e modificar valores monetários para tipo double.  
Verificação de Valores Nulos:  
Identificar registros NULL em Super_ssn, associando-os a possíveis gerentes.  
Identificar NULL em Mgr_ssn na tabela departament. Caso existam, preencher com dados fictícios para completar as relações.  
Análise e Separação de Colunas Complexas: Separar colunas como Nome Completo em Nome e Sobrenome.  
Junções e Mesclas:  
Mesclar employee com departament para associar colaboradores ao departamento, removendo colunas desnecessárias.  
Criar uma tabela para listar colaboradores e seus gerentes diretos.  
Combinar as colunas de Nome e Sobrenome em uma única coluna de Nome Completo.  
Unificar o nome e localização do departamento para criar combinações únicas departamento-local.  
Agrupamento de Dados: Agrupar colaboradores por gerente para facilitar análises de equipe e supervisão.  
# 5. Explicação das Mesclas
No contexto de Power BI, as operações de mescla foram escolhidas para manter as associações originais das tabelas sem duplicações. Utilizar mescla em vez de atribuição direta permite que as tabelas mantenham a integridade referencial e fiquem consistentes para o modelo estrela.  

Estrutura do Banco de Dados  
Tabelas:  
employee: Contém informações sobre cada colaborador, como SSN, nome, endereço, salário e SSN do supervisor.  
departament: Armazena dados sobre departamentos, como nome, número, SSN do gerente e datas de criação.  
Consultas SQL Usadas para Transformações  
Aqui estão algumas das consultas SQL usadas nas transformações de dados:  
  
Consulta para identificar gerentes (com NULL em Super_ssn):  

sql  
Copiar código  
SELECT * FROM employee WHERE Super_ssn IS NULL;  
Junção entre employee e departament:  
  
sql  
Copiar código  
SELECT e.*, d.Dname AS Department_Name  
FROM employee e  
JOIN departament d ON e.Dno = d.Dnumber;  
Contagem de colaboradores por gerente:  

sql  
Copiar código  
SELECT Super_ssn, COUNT(*) AS Num_Employees  
FROM employee  
GROUP BY Super_ssn;  
Licença  
Este projeto é apenas para fins educacionais.  
