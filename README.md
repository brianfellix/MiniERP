# Mini ERP em Oracle PL/SQL

Sistema de gestão empresarial (ERP) desenvolvido em **Oracle Database**, estruturado com modelagem relacional, triggers de automação e auditoria, views analíticas e procedures em PL/SQL para regras de negócio e controle transacional ponta a ponta.

## Estrutura do Projeto

```text
MiniERP/
├── database/
│   ├── environment/
│   │   └── 00_table_space.sql
│   ├── tables/
│   │   └── 01_tabelas.sql
│   ├── triggers/
│   │   ├── 02_TRIGGERS_AUTO.sql
│   │   ├── 13_TRIGGERS_BLOQ_USUARIO.sql
│   │   └── 14_TRIGGER_AUDIT_SALARIO.sql
│   ├── procedures/
│   │   ├── 04_proc_copia_mat.sql
│   │   ├── 05_PROC_PLAN_ORDEM.sql
│   │   ├── 06_PROC_GER_PED_COMPRAS.sql
│   │   ├── 07_PROC_ESTOQUE.sql
│   │   ├── 08_PROC_GERA_NF.sql
│   │   ├── 09_PROC_INTEGR_NF_ESTOQUE.sql
│   │   ├── 10_PROC_INTEGR_FIN.SQL
│   │   ├── 11_PROC_APONTAMENTO.sql
│   │   └── 12_PROC_FOLHA.sql
│   └── views/
│       ├── 15_VIEWS_FUNCIONARIO.sql
│       ├── 16_VIEWS_FATURAMENTO.sql
│       ├── 17_VIEWS_NECESSIDADES.sql
│       ├── 18_VIEWS_FIN.sql
│       ├── 19_VIEWS_CUSTO.sql
│       └── 20_VIEWS_CANAL_VENDAS.sql
├── seeds/
│   └── 03_CARGAS.sql
├── docs/
│   └── mer.vsdx
└── README.md
```

## Objetivo

Simular a arquitetura completa de um ERP corporativo diretamente no banco de dados Oracle, integrando os principais fluxos operacionais, financeiros e de recursos humanos:

* Planejamento de necessidades de materiais (MRP) e ordens de produção
* Gestão de compras, movimentação de estoque e apontamento de produção
* Emissão de Nota Fiscal (NF) com integração automática ao estoque e financeiro
* Cálculo de folha de pagamento, auditoria salarial e controle de acesso de usuários
* Camada de inteligência gerencial (Views) para custos, faturamento e canais de venda

## Tecnologias Utilizadas

* Oracle Database
* Oracle SQL & PL/SQL
* Oracle SQL Developer
* Microsoft Visio (Modelo Entidade-Relacionamento - MER)
* Git & GitHub

## Módulos e Arquitetura

### 1. Ambiente, Tabelas e Carga Inicial (`00` a `03`)
* **Tablespace & DDL:** Configuração do ambiente físico (`00_table_space.sql`) e criação das entidades relacionais (`01_tabelas.sql`).
* **Automação & Seeds:** Triggers de sequenciamento e preenchimento automático (`02_TRIGGERS_AUTO.sql`) seguidas da carga inicial de dados para testes (`03_CARGAS.sql`).

### 2. Regras de Negócio em PL/SQL (`04` a `12`)
* **Produção & Suprimentos:** Cópia de estrutura de materiais (`04`), planejamento de ordens (`05`), geração de pedidos de compra (`06`), controle de estoque (`07`) e apontamento de produção (`11`).
* **Faturamento & Financeiro:** Geração de Nota Fiscal (`08`), baixa/entrada automática no estoque via NF (`09`) e integração com títulos financeiros (`10`).
* **Recursos Humanos:** Processamento e cálculo da folha de pagamento (`12`).

### 3. Segurança, Auditoria e Views (`13` a `20`)
* **Governança:** Triggers para bloqueio de usuários (`13`) e trilha de auditoria para alterações salariais (`14`).
* **Relatórios Gerenciais:** Views consolidadas para quadro de funcionários (`15`), faturamento (`16`), necessidades de materiais (`17`), financeiro (`18`), apuração de custos (`19`) e canais de venda (`20`).

## Como Utilizar (Ordem de Execução)

Os scripts estão numerados sequencialmente (`00` a `20`) para respeitar todas as dependências entre objetos:

1. **Ambiente e Estrutura:** Execute `database/environment/00_table_space.sql` e `database/tables/01_tabelas.sql`.
2. **Triggers Base e Dados:** Execute `database/triggers/02_TRIGGERS_AUTO.sql` e `seeds/03_CARGAS.sql`.
3. **Procedures de Negócio:** Compile os scripts de `04` a `12` dentro de `database/procedures/`.
4. **Auditoria e Views:** Execute as triggers de segurança (`13` e `14`) e as views analíticas (`15` a `20`).

> **Nota:** O diagrama completo do banco de dados está disponível em `docs/mer.vsdx`.

## Licença

Projeto desenvolvido para fins de estudo, portfólio técnico e aprofundamento em arquitetura Oracle PL/SQL.
