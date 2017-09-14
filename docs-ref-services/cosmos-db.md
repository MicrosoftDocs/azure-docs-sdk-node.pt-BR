---
title: "Módulos do Azure Cosmos DB para Node.js"
description: "Referência dos módulos do Azure Cosmos DB para Node.js"
keywords: Azure,SDK,API, Cosmos DB, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Cosmos DB
ms.openlocfilehash: 1f545f89b5304b611dbe1ed9cb86052c112f13c1
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-cosmos-db-modules-for-nodejs"></a><span data-ttu-id="222aa-104">Módulos do Azure Cosmos DB para Node.js</span><span class="sxs-lookup"><span data-stu-id="222aa-104">Azure Cosmos DB Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="222aa-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="222aa-105">Overview</span></span>

<span data-ttu-id="222aa-106">O BD Cosmos do Azure é o multimodelo de banco de dados distribuído globalmente da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="222aa-106">Azure Cosmos DB is Microsoft's globally distributed, multi-model database.</span></span> <span data-ttu-id="222aa-107">O Azure Cosmos DB permite que você dimensione a taxa de transferência e o armazenamento de maneira elástica e independente em qualquer número de regiões geográficas do Azure.</span><span class="sxs-lookup"><span data-stu-id="222aa-107">Azure Cosmos DB enables you to elastically and independently scale throughput and storage across any number of Azure's geographic regions.</span></span> <span data-ttu-id="222aa-108">Ele oferece garantias de taxa de transferência, disponibilidade, latência e consistência com SLAs (contratos de nível de serviço) abrangentes, algo que nenhum outro serviço de banco de dados pode oferecer.</span><span class="sxs-lookup"><span data-stu-id="222aa-108">It offers throughput, latency, availability, and consistency guarantees with comprehensive service level agreements (SLAs), something no other database service can offer.</span></span>

<span data-ttu-id="222aa-109">O BD Cosmos do Azure contém um mecanismo de banco de dados otimizado para gravação, governado por recursos, independente de esquemas que dá suporte a vários modelos de dados de forma nativa: chave-valor, documentos, gráficos e colunares.</span><span class="sxs-lookup"><span data-stu-id="222aa-109">Azure Cosmos DB contains a write optimized, resource governed, schema-agnostic database engine that natively supports multiple data models: key-value, documents, graphs, and columnar.</span></span> <span data-ttu-id="222aa-110">Ele também dá suporte a várias APIs para acessar dados incluindo MongoDB, SQL do DocumentDB, Gremlin (versão prévia) e Tabelas do Azure (versão prévia), de forma extensível.</span><span class="sxs-lookup"><span data-stu-id="222aa-110">It also supports many APIs for accessing data including MongoDB, DocumentDB SQL, Gremlin (preview), and Azure Tables (preview), in an extensible manner.</span></span>

## <a name="management-package"></a><span data-ttu-id="222aa-111">Pacote de Gerenciamento</span><span class="sxs-lookup"><span data-stu-id="222aa-111">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="222aa-112">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="222aa-112">Install the npm module</span></span> 

<span data-ttu-id="222aa-113">Instalar o módulo npm do Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="222aa-113">Install the Azure Cosmos DB npm module</span></span>

```bash
npm install azure-arm-documentdb
```

### <a name="example"></a><span data-ttu-id="222aa-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="222aa-114">Example</span></span>

<span data-ttu-id="222aa-115">Este exemplo lista todas as contas do Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="222aa-115">This example lists all Cosmos DB accounts.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const documentDBManagementClient = require('azure-arm-documentdb');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const documentDbClient = new documentDBManagementClient(credentials, subscriptionId);
  documentDbClient.databaseAccounts
    .list()
    .then(databaseAccounts => console.log('Retrieved database accounts: ', databaseAccounts));
});
```

## <a name="samples"></a><span data-ttu-id="222aa-116">Exemplos</span><span class="sxs-lookup"><span data-stu-id="222aa-116">Samples</span></span>

* [<span data-ttu-id="222aa-117">Desenvolvimento de um aplicativo Node.js usando o Azure Cosmos DB - DocumentDB</span><span class="sxs-lookup"><span data-stu-id="222aa-117">Developing a Node.js app using Azure Cosmos DB - DocumentDB</span></span>](https://azure.microsoft.com/resources/samples/azure-cosmos-db-documentdb-nodejs-getting-started/)
* [<span data-ttu-id="222aa-118">Desenvolvimento de um aplicativo Node.js usando o Azure Cosmos DB - Gremlin</span><span class="sxs-lookup"><span data-stu-id="222aa-118">Developing a Node.js app using Azure Cosmos DB - Gremlin</span></span>](https://azure.microsoft.com/resources/samples/azure-cosmos-db-graph-nodejs-getting-started/)

<span data-ttu-id="222aa-119">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="222aa-119">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
