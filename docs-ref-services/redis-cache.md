---
title: "Módulos de Cache Redis do Azure para Node.js"
description: "Referência dos módulos do Cache Redis do Azure para Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Redis Cache
ms.openlocfilehash: 5d3a410fefcf6840181701763346fbfe08fe023b
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/26/2018
---
# <a name="azure-redis-cache-modules-for-nodejs"></a><span data-ttu-id="36928-103">Módulos de Cache Redis do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="36928-103">Azure Redis Cache modules for Node.js</span></span>

<span data-ttu-id="36928-104">O Cache Redis do Azure se baseia no popular projeto Redis de software livre.</span><span class="sxs-lookup"><span data-stu-id="36928-104">Azure Redis Cache is based on the popular open source Redis project.</span></span> <span data-ttu-id="36928-105">Ele oferece acesso a uma instância do Redis segura e dedicada, gerenciada pela Microsoft e acessível desde os seus aplicativos do Azure.</span><span class="sxs-lookup"><span data-stu-id="36928-105">It gives you access to a secure, dedicated Redis instance, managed by Microsoft and accessible from your Azure apps.</span></span>

<span data-ttu-id="36928-106">O Redis é um repositório de chave-valor avançado, no qual as chaves podem conter estruturas de dados como cadeias de caracteres, hashes, listas, conjuntos e conjuntos classificados.</span><span class="sxs-lookup"><span data-stu-id="36928-106">Redis is an advanced key-value store, where keys can contain data structures such as strings, hashes, lists, sets, and sorted sets.</span></span> <span data-ttu-id="36928-107">O Redis dá suporte a um conjunto de operações atômicas nesses tipos de dados.</span><span class="sxs-lookup"><span data-stu-id="36928-107">Redis supports a set of atomic operations on these data types.</span></span>

<span data-ttu-id="36928-108">Saiba mais sobre o [Cache Redis do Azure](https://docs.microsoft.com/azure/redis-cache/).</span><span class="sxs-lookup"><span data-stu-id="36928-108">Learn more about [Azure Redis Cache](https://docs.microsoft.com/azure/redis-cache/).</span></span>

## <a name="client-package"></a><span data-ttu-id="36928-109">Pacote de cliente</span><span class="sxs-lookup"><span data-stu-id="36928-109">Client package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="36928-110">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="36928-110">Install the npm module</span></span>

<span data-ttu-id="36928-111">Usar npm para instalar o módulo do Redis para Node.js</span><span class="sxs-lookup"><span data-stu-id="36928-111">Use npm to install the Redis module for Node.js</span></span>

```bash
npm install redis
```

### <a name="example"></a><span data-ttu-id="36928-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="36928-112">Example</span></span>

<span data-ttu-id="36928-113">Este exemplo conecta a uma instância do Cache Redis do Azure, armazena um par de chave/valor e, em seguida, lê o valor armazenado por sua chave.</span><span class="sxs-lookup"><span data-stu-id="36928-113">This example connects to an Azure Redis Cache instance, stores a key/value pair and then reads the stored value by its key.</span></span>

```javascript
const redis = require('redis');

const client = redis.createClient(6380, '<name>.redis.cache.windows.net', {
  auth_pass: '<key>',
  tls: { servername: '<name>.redis.cache.windows.net' }
});

client.set('key1', 'value', (err, reply) => {
  console.log(reply);
});

client.get('key1', (err, reply) => {
  console.log(reply);
});
```

## <a name="management-package"></a><span data-ttu-id="36928-114">Pacote de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="36928-114">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="36928-115">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="36928-115">Install the npm module</span></span>

<span data-ttu-id="36928-116">Usar npm para instalar os módulos do Cache Redis do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="36928-116">Use npm to install the Azure Redis Cache modules for Node.js</span></span>

```bash
npm install azure-arm-rediscache
```

### <a name="example"></a><span data-ttu-id="36928-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="36928-117">Example</span></span>

<span data-ttu-id="36928-118">Este exemplo autentica no Azure e lista todas as instâncias de Cache Redis em um grupo de recursos especificado.</span><span class="sxs-lookup"><span data-stu-id="36928-118">This example authenticates to Azure and lists all Redis Cache instances in a specified resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const AzureMgmtRedisCache = require('azure-arm-rediscache');

msRestAzure.interactiveLogin().then(credentials => {
  const client = new AzureMgmtRedisCache(credentials, 'my-subscription-id');
  client.redis.listByResourceGroup('testResourceGroup').then(result => {
    console.log(result);
  });
});
```


## <a name="samples"></a><span data-ttu-id="36928-119">Exemplos</span><span class="sxs-lookup"><span data-stu-id="36928-119">Samples</span></span>

* [<span data-ttu-id="36928-120">Como usar o Cache Redis do Azure com Node.js</span><span class="sxs-lookup"><span data-stu-id="36928-120">How to use Azure Redis Cache with Node.js</span></span>](https://docs.microsoft.com/azure/redis-cache/cache-nodejs-get-started)

<span data-ttu-id="36928-121">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="36928-121">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
