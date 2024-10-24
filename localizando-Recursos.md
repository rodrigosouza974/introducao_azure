---

# Localizando Serviços por Categoria no Azure

Este guia ajuda você a navegar pelos serviços do Azure, organizando-os por categoria, para facilitar a localização do serviço adequado às suas necessidades de infraestrutura, banco de dados, rede, segurança e muito mais.

## Introdução

O Azure oferece centenas de serviços em diversas categorias, como Computação, Redes, Banco de Dados, Armazenamento, IA, Segurança, e outros. Você pode navegar por esses serviços diretamente no [Portal do Azure](https://portal.azure.com) ou usando a **CLI do Azure** para filtrar e identificar os serviços que melhor atendem ao seu projeto.

## Localizando Serviços no Portal do Azure

### 1. Acessar o Portal do Azure

Primeiramente, acesse o [Portal do Azure](https://portal.azure.com) e faça login com sua conta.

### 2. Navegar pelo Catálogo de Serviços

No menu lateral esquerdo, clique em **"Criar um recurso"** para abrir o catálogo de serviços do Azure. Você verá as seguintes categorias principais:

- **Computação**: Para criar máquinas virtuais, contêineres, funções e aplicativos escaláveis. Exemplos:
  - [Máquinas Virtuais](https://learn.microsoft.com/azure/virtual-machines/)
  - [App Service](https://learn.microsoft.com/azure/app-service/)
  - [AKS (Azure Kubernetes Service)](https://learn.microsoft.com/azure/aks/)

- **Rede**: Serviços que permitem criar redes virtuais, balanceadores de carga e VPNs. Exemplos:
  - [Virtual Network](https://learn.microsoft.com/azure/virtual-network/)
  - [Azure Load Balancer](https://learn.microsoft.com/azure/load-balancer/)
  - [Azure Firewall](https://learn.microsoft.com/azure/firewall/)

- **Banco de Dados**: Para gerenciar bancos de dados SQL, NoSQL e serviços de análise de dados. Exemplos:
  - [Azure SQL Database](https://learn.microsoft.com/azure/sql-database/)
  - [Cosmos DB](https://learn.microsoft.com/azure/cosmos-db/)
  - [Azure Database for MySQL](https://learn.microsoft.com/azure/mysql/)

- **Armazenamento**: Oferece armazenamento de dados estruturados e não estruturados. Exemplos:
  - [Azure Storage](https://learn.microsoft.com/azure/storage/)
  - [Azure Blob Storage](https://learn.microsoft.com/azure/storage/blobs/)
  - [Azure File Storage](https://learn.microsoft.com/azure/storage/files/)

- **IA e Machine Learning**: Serviços relacionados à inteligência artificial, aprendizado de máquina e análise de dados. Exemplos:
  - [Azure Cognitive Services](https://learn.microsoft.com/azure/cognitive-services/)
  - [Azure Machine Learning](https://learn.microsoft.com/azure/machine-learning/)
  - [Azure Bot Service](https://learn.microsoft.com/azure/bot-service/)

- **Segurança**: Soluções para garantir segurança e conformidade no seu ambiente Azure. Exemplos:
  - [Azure Security Center](https://learn.microsoft.com/azure/security-center/)
  - [Azure Active Directory](https://learn.microsoft.com/azure/active-directory/)
  - [Azure Key Vault](https://learn.microsoft.com/azure/key-vault/)

### 3. Filtrar por Categoria e Subcategorias

No catálogo, você pode usar a barra de busca ou clicar nas categorias específicas para refinar sua pesquisa e localizar o serviço desejado.

- **Dica**: Utilize a busca rápida na barra superior para localizar um serviço diretamente por nome, por exemplo, digitar "Cosmos DB" mostrará o serviço de banco de dados NoSQL.

Para mais detalhes sobre como explorar o catálogo de serviços, consulte a documentação oficial: [Navegando no Portal do Azure](https://learn.microsoft.com/azure/azure-portal/azure-portal-overview)

## Localizando Serviços Usando a CLI do Azure

Você também pode listar e localizar serviços do Azure pela **CLI**. Aqui estão alguns comandos úteis para descobrir serviços em diferentes categorias.

### 1. Listar Serviços Disponíveis

Para ver a lista de todos os serviços e recursos disponíveis no Azure, execute o seguinte comando:

```bash
az provider list --output table
```

Esse comando exibirá os provedores de serviços registrados no Azure.

### 2. Filtrar Serviços por Categoria

Você pode listar os serviços por grupo de recursos ou provedores específicos. Por exemplo, para localizar serviços relacionados à "Microsoft.Compute" (serviços de computação, como máquinas virtuais), use:

```bash
az resource list --resource-type Microsoft.Compute/virtualMachines --output table
```

### 3. Ver Detalhes de Um Serviço

Para visualizar os detalhes de um serviço específico, como uma máquina virtual, use o comando abaixo, substituindo `<resource-group>` pelo nome do grupo de recursos e `<vm-name>` pelo nome da máquina virtual:

```bash
az vm show --resource-group <resource-group> --name <vm-name> --output json
```

Para mais informações sobre comandos da CLI do Azure, consulte: [Documentação da CLI do Azure](https://learn.microsoft.com/cli/azure/)

## Exemplos de Categorias e Serviços Populares

- **DevOps**:
  - [Azure DevOps](https://azure.microsoft.com/services/devops/)
  - [GitHub Actions](https://docs.github.com/actions)

- **Big Data**:
  - [Azure Synapse Analytics](https://learn.microsoft.com/azure/synapse-analytics/)
  - [HDInsight](https://learn.microsoft.com/azure/hdinsight/)

- **Mobilidade**:
  - [App Center](https://learn.microsoft.com/appcenter/)
  - [Azure Notification Hubs](https://learn.microsoft.com/azure/notification-hubs/)

## Recursos Complementares

- **Microsoft Learn**: [Treinamento em Azure](https://learn.microsoft.com/training/azure/)
- **Azure Architecture Center**: [Modelos e Melhores Práticas](https://learn.microsoft.com/azure/architecture/)
- **Preços do Azure**: [Calculadora de Preços](https://azure.microsoft.com/pricing/calculator/)

---
