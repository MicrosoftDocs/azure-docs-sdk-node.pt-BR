---
title: Módulos de Armazenamento do Azure para Node.js
description: Referência dos módulos do Armazenamento do Azure para Node.js
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: storage
ms.openlocfilehash: b94c6fbb50e656e0dcc542236afe791c7ddc9be4
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/26/2018
ms.locfileid: "28116891"
---
# <a name="azure-storage-modules-for-nodejs"></a>Módulos de Armazenamento do Azure para Node.js

Use o módulo de cliente do Armazenamento do Azure para:

- Ler e gravar objetos e arquivos do [Armazenamento de Blobs do Azure](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-blob-storage)
- Enviar e receber mensagens entre aplicativos conectados à nuvem com o [Armazenamento de Filas do Azure](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-queues)
- Ler e gravar dados estruturados grandes com o [Armazenamento de Tabelas do Azure](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-table-storage)

Criar, atualizar e gerenciar contas de Armazenamento do Azure e consultar e regenerar chaves de acesso dos seus aplicativos Node.js com os módulos de gerenciamento.

## <a name="client-package"></a>Pacote de Cliente

### <a name="install-the-npm-module"></a>Instalar o módulo npm

Instalar o módulo npm de cliente de armazenamento do Azure

```bash
npm install azure-storage
```

### <a name="example"></a>Exemplo

Este exemplo cria um contêiner de armazenamento e carrega um arquivo local `data.txt` para ele.

```javascript
const azure = require('azure-storage');
const blobService = azure.createBlobService(storageConnectionString);

const container = 'taskcontainer';
const task = 'taskblob';
const filename = 'data.txt';

blobService.createContainerIfNotExists(container, error => {
  if (error) return console.log(error);
  blobService.createBlockBlobFromLocalFile(
    container,
    task,
    filename,
    (error, result) => {
      if (error) return console.log(error);
      console.dir(result, { depth: null, colors: true });
    }
  );
});
```

## <a name="management-package"></a>Pacote de Gerenciamento

### <a name="install-the-npm-module"></a>Instalar o módulo npm 

Instalar o módulo npm de gerenciamento de armazenamento do Azure

```bash
npm install azure-arm-storage
```

### <a name="example"></a>Exemplo

Este exemplo lista as contas de armazenamento.

```javascript
const msRestAzure = require('ms-rest-azure');
const storageManagementClient = require('azure-arm-storage');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new storageManagementClient(
      credentials,
      subscriptionId
    );
    return client.storageAccounts.list();
  })
  .then(accounts => console.dir(accounts, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a>Exemplos

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/storage-samples.md)]

Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.
