---
title: Módulos de Cache Redis do Azure para Node.js
description: Referência dos módulos do Cache Redis do Azure para Node.js
author: wesmc7777
ms.author: wesmc
manager: cfowler
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Redis Cache
ms.openlocfilehash: afeee19cb79b54561b6cbef4a79de8b1606adb4d
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34265057"
---
# <a name="azure-redis-cache-modules-for-nodejs"></a>Módulos de Cache Redis do Azure para Node.js

O Cache Redis do Azure se baseia no popular projeto Redis de software livre. Ele oferece acesso a uma instância do Redis segura e dedicada, gerenciada pela Microsoft e acessível desde os seus aplicativos do Azure.

O Redis é um repositório de chave-valor avançado, no qual as chaves podem conter estruturas de dados como cadeias de caracteres, hashes, listas, conjuntos e conjuntos classificados. O Redis dá suporte a um conjunto de operações atômicas nesses tipos de dados.

Saiba mais sobre o [Cache Redis do Azure](https://docs.microsoft.com/azure/redis-cache/).

## <a name="client-package"></a>Pacote de cliente

### <a name="install-the-npm-module"></a>Instalar o módulo npm

Usar npm para instalar o módulo do Redis para Node.js

```bash
npm install redis
```

### <a name="example"></a>Exemplo

Este exemplo conecta a uma instância do Cache Redis do Azure, armazena um par de chave/valor e, em seguida, lê o valor armazenado por sua chave.

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

## <a name="management-package"></a>Pacote de gerenciamento

### <a name="install-the-npm-module"></a>Instalar o módulo npm

Usar npm para instalar os módulos do Cache Redis do Azure para Node.js

```bash
npm install azure-arm-rediscache
```

### <a name="example"></a>Exemplo

Este exemplo autentica no Azure e lista todas as instâncias de Cache Redis em um grupo de recursos especificado.

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


## <a name="samples"></a>Exemplos

* [Como usar o Cache Redis do Azure com Node.js](https://docs.microsoft.com/azure/redis-cache/cache-nodejs-get-started)

Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.
