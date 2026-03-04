# Projeto-ABAP-CDS-Pedidos-e-Produtos
Descrição Geral:
Este projeto contém três ABAP CDS Views relacionadas entre si, que permitem consolidar informações de pedidos de venda e produtos em diferentes níveis de complexidade. A hierarquia das views é:

ZI_CDS_PRODUCT – visão básica dos produtos.

ZI_CDS_ORDER – visão básica dos itens de pedido.

ZI_DLCDS_ORDERITEM_PRODUCT – visão composta que une itens de pedido e produtos, pronta para relatórios e análises mais completas.

1. ZI_CDS_PRODUCT (Produto – Básico)

Descrição:
Representa os produtos da empresa, fornecendo informações essenciais como tipo, descrição e dados de auditoria. Serve como base para associações com outras views.

Campos principais:

Product – identificador único do produto.

ProductType – tipo do produto.

Description – descrição do produto.

AuthorizationGroup – grupo de autorização.

CreationDataTime – data e hora de criação.

Objetivo:
Fornecer dados padronizados de produtos, garantindo consistência para views compostas e análises de pedidos.

2. ZI_CDS_ORDER (Itens de Pedido – Básico)

Descrição:
Representa os itens de pedido (zdlcdst_order_it) em nível básico, sem associações externas, fornecendo informações essenciais de cada item do pedido.

Campos principais:

SalesOrder, SalesOrderItem – identificadores do pedido e item.

Product, ProductQuantity, ProductUnity – informações do produto e quantidade.

TotalValue, Currency – valor total e moeda.

CreationDate, CreationUser, LastChangedBy, LastChangedFrom – informações de auditoria.

Objetivo:
Servir como base para análises simples ou como referência para views compostas.

3. ZI_DLCDS_ORDERITEM_PRODUCT (Itens de Pedido + Produto – Composto)

Descrição:
View composta que une os itens de pedido (ZI_CDS_ORDER) com informações do produto (ZI_CDS_PRODUCT) por meio de uma associação 1:1. Permite uma visão integrada e pronta para relatórios, ALV ou consumo por aplicações Fiori/ABAP.

Campos principais:

Todos os campos da view básica de pedido.

Campos do produto via associação _Product, incluindo Description.

Anotações de semântica para unidade de medida e moeda.

Objetivo:
Prover uma visão completa de itens de pedido com dados do produto, facilitando consultas, relatórios e análises avançadas.

Tecnologias e Conceitos Aplicados

ABAP CDS Views (básicas e compostas)

Associações 1:1 entre entidades

Semântica de dados (@Semantics.quantity.unitOfMeasure, @Semantics.amount.currencyCode)

Metadados avançados (@AbapCatalog.viewEnhancementCategory, @AccessControl.authorizationCheck, @Metadata.ignorePropagatedAnnotations)

Organização hierárquica de dados, permitindo views básicas, referenciais e compostas.
