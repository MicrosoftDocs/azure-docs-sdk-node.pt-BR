---
title: Módulos do Azure Cosmos DB para Node.js
description: Referência dos módulos do Azure Cosmos DB para Node.js
author: SnehaGunda
ms.author: sngun
manager: kfile
ms.date: 03/20/2018
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Cosmos DB
ms.openlocfilehash: 2e2813bb3b213de4066b2a3bc971586667a83f68
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51439430"
---
# <a name="azure-cosmos-db-modules-for-nodejs"></a><span data-ttu-id="b67b3-103">Módulos do Azure Cosmos DB para Node.js</span><span class="sxs-lookup"><span data-stu-id="b67b3-103">Azure Cosmos DB Modules for Node.js</span></span>

<span data-ttu-id="b67b3-104">O BD Cosmos do Azure é o multimodelo de banco de dados distribuído globalmente da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b67b3-104">Azure Cosmos DB is Microsoft's globally distributed, multi-model database.</span></span> <span data-ttu-id="b67b3-105">O Azure Cosmos DB permite que você dimensione a taxa de transferência e o armazenamento de maneira elástica e independente em qualquer número de regiões geográficas do Azure.</span><span class="sxs-lookup"><span data-stu-id="b67b3-105">Azure Cosmos DB enables you to elastically and independently scale throughput and storage across any number of Azure's geographic regions.</span></span> <span data-ttu-id="b67b3-106">Ele oferece garantias de taxa de transferência, disponibilidade, latência e consistência com SLAs (contratos de nível de serviço) abrangentes, algo que nenhum outro serviço de banco de dados pode oferecer.</span><span class="sxs-lookup"><span data-stu-id="b67b3-106">It offers throughput, latency, availability, and consistency guarantees with comprehensive service level agreements (SLAs), something no other database service can offer.</span></span>

<span data-ttu-id="b67b3-107">O Azure Cosmos DB contém um mecanismo de banco de dados otimizado para gravação, governado por recursos, independente de esquemas que dá suporte a vários modelos de dados de forma nativa: chave-valor, documentos, grafos e colunares.</span><span class="sxs-lookup"><span data-stu-id="b67b3-107">Azure Cosmos DB contains a write optimized, resource governed, schema-agnostic database engine that natively supports multiple data models: key-value, documents, graphs, and columnar.</span></span> <span data-ttu-id="b67b3-108">Ele também dá suporte a muitas APIs para acessar dados, incluindo MongoDB, SQL, Gremlin/Graph, Tabelas do Azure e Cassandra (versão prévia), de forma extensível.</span><span class="sxs-lookup"><span data-stu-id="b67b3-108">It also supports many APIs for accessing data including MongoDB, SQL, Gremlin/Graph, Azure Tables, and Cassandra (preview) in an extensible manner.</span></span>

## <a name="management-package"></a><span data-ttu-id="b67b3-109">Pacote de Gerenciamento</span><span class="sxs-lookup"><span data-stu-id="b67b3-109">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="b67b3-110">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="b67b3-110">Install the npm module</span></span> 

<span data-ttu-id="b67b3-111">Instalar o módulo npm do Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="b67b3-111">Install the Azure Cosmos DB npm module.</span></span>

```bash
npm install azure-arm-documentdb
```

### <a name="example"></a><span data-ttu-id="b67b3-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b67b3-112">Example</span></span>

<span data-ttu-id="b67b3-113">Este exemplo lista todas as contas do Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="b67b3-113">This example lists all Azure Cosmos DB accounts.</span></span>

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

## <a name="samples"></a><span data-ttu-id="b67b3-114">Exemplos</span><span class="sxs-lookup"><span data-stu-id="b67b3-114">Samples</span></span>

* [<span data-ttu-id="b67b3-115">Desenvolvimento de um aplicativo Node.js usando o Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="b67b3-115">Developing a Node.js app using Azure Cosmos DB</span></span>](https://azure.microsoft.com/resources/samples/azure-cosmos-db-documentdb-nodejs-getting-started/)
* [<span data-ttu-id="b67b3-116">Desenvolvimento de um aplicativo Node.js usando o Azure Cosmos DB - Gremlin</span><span class="sxs-lookup"><span data-stu-id="b67b3-116">Developing a Node.js app using Azure Cosmos DB - Gremlin</span></span>](https://azure.microsoft.com/resources/samples/azure-cosmos-db-graph-nodejs-getting-started/)

<span data-ttu-id="b67b3-117">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="b67b3-117">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
