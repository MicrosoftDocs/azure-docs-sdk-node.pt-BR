---
title: "Módulos do PostgreSQL do Azure para Node.js"
description: "Referência dos módulos do Azure PostgreSQL para Node.js"
keywords: Azure, Node, SDK, API, nodejs, javascript, banco de dados, PostgreSQL
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: postgresql
ms.openlocfilehash: a5130c96b3ae922358b6898c15510282fbaa97f0
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-postgresql-modules-for-nodejs"></a><span data-ttu-id="448f0-104">Módulos do PostgreSQL do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="448f0-104">Azure PostgreSQL modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="448f0-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="448f0-105">Overview</span></span>

<span data-ttu-id="448f0-106">A biblioteca de cliente recomendada para acessar o banco de dados PostgreSQL é a [biblioteca de conexão Node.js para Banco de Dados do Azure para PostgreSQL](https://www.npmjs.com/package/pg), que é um software livre.</span><span class="sxs-lookup"><span data-stu-id="448f0-106">The recommended client library for accessing Azure Database for PostgreSQL is the open-source [Node.js connection library for Azure Database for PostgreSQL](https://www.npmjs.com/package/pg).</span></span> <span data-ttu-id="448f0-107">Essa biblioteca é um cliente PostgreSQL sem bloqueio para Node.js, dando suporte a JavaScript puro e associações libpq nativas opcionais.</span><span class="sxs-lookup"><span data-stu-id="448f0-107">This library is a non-blocking PostgreSQL client for Node.js, supporting pure JavaScript and optional native libpq bindings.</span></span>

<span data-ttu-id="448f0-108">Saiba mais sobre o [Banco de Dados do Azure para PostgreSQL](https://docs.microsoft.com/azure/postgresql/)</span><span class="sxs-lookup"><span data-stu-id="448f0-108">Learn more about [Azure Database for PostgreSQL](https://docs.microsoft.com/azure/postgresql/)</span></span>

## <a name="client-package"></a><span data-ttu-id="448f0-109">Pacote de cliente</span><span class="sxs-lookup"><span data-stu-id="448f0-109">Client package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="448f0-110">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="448f0-110">Install the npm module</span></span>

<span data-ttu-id="448f0-111">Usar npm para instalar o módulo de cliente PostgreSQL.</span><span class="sxs-lookup"><span data-stu-id="448f0-111">Use npm to install the PostgreSQL client module.</span></span>

```bash
npm install pg
```   

### <a name="example"></a><span data-ttu-id="448f0-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="448f0-112">Example</span></span>

<span data-ttu-id="448f0-113">Este exemplo abre uma conexão de cliente e executa uma consulta simples.</span><span class="sxs-lookup"><span data-stu-id="448f0-113">This example opens a client connection and executes a simple query.</span></span>

```javascript
const pg = require('pg');

const connectionString =
  'postgres://{username}@{server-name}:{password}@{server-name}.postgres.database.azure.com:5432/{database-name}?ssl=true';

const client = new pg.Client(connectionString);
client.connect();

const query = 'SELECT * FROM {table-name}';
client.query(query, (err, res) => {
  console.log(res);
});
```

## <a name="samples"></a><span data-ttu-id="448f0-114">Exemplos</span><span class="sxs-lookup"><span data-stu-id="448f0-114">Samples</span></span>

[!INCLUDE [node-postgresql-samples](../docs-ref-conceptual/includes/postgresql-samples.md)]

<span data-ttu-id="448f0-115">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="448f0-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
