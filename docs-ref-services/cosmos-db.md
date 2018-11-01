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
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2018
ms.locfileid: "50334334"
---
# <a name="azure-cosmos-db-modules-for-nodejs"></a>Módulos do Azure Cosmos DB para Node.js

O BD Cosmos do Azure é o multimodelo de banco de dados distribuído globalmente da Microsoft. O Azure Cosmos DB permite que você dimensione a taxa de transferência e o armazenamento de maneira elástica e independente em qualquer número de regiões geográficas do Azure. Ele oferece garantias de taxa de transferência, disponibilidade, latência e consistência com SLAs (contratos de nível de serviço) abrangentes, algo que nenhum outro serviço de banco de dados pode oferecer.

O Azure Cosmos DB contém um mecanismo de banco de dados otimizado para gravação, governado por recursos, independente de esquemas que dá suporte a vários modelos de dados de forma nativa: chave-valor, documentos, grafos e colunares. Ele também dá suporte a muitas APIs para acessar dados, incluindo MongoDB, SQL, Gremlin/Graph, Tabelas do Azure e Cassandra (versão prévia), de forma extensível.

## <a name="management-package"></a>Pacote de Gerenciamento

### <a name="install-the-npm-module"></a>Instalar o módulo npm 

Instalar o módulo npm do Azure Cosmos DB.

```bash
npm install azure-arm-documentdb
```

### <a name="example"></a>Exemplo

Este exemplo lista todas as contas do Azure Cosmos DB.

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

## <a name="samples"></a>Exemplos

* [Desenvolvimento de um aplicativo Node.js usando o Azure Cosmos DB](https://azure.microsoft.com/resources/samples/azure-cosmos-db-documentdb-nodejs-getting-started/)
* [Desenvolvimento de um aplicativo Node.js usando o Azure Cosmos DB - Gremlin](https://azure.microsoft.com/resources/samples/azure-cosmos-db-graph-nodejs-getting-started/)

Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.
