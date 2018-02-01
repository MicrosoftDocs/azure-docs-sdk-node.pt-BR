---
title: "Módulos de Armazenamento do Azure para Node.js"
description: "Referência dos módulos do Armazenamento do Azure para Node.js"
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
---
# <a name="azure-storage-modules-for-nodejs"></a><span data-ttu-id="d55dc-103">Módulos de Armazenamento do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="d55dc-103">Azure Storage modules for Node.js</span></span>

<span data-ttu-id="d55dc-104">Use o módulo de cliente do Armazenamento do Azure para:</span><span class="sxs-lookup"><span data-stu-id="d55dc-104">Use the Azure Storage client module to:</span></span>

- <span data-ttu-id="d55dc-105">Ler e gravar objetos e arquivos do [Armazenamento de Blobs do Azure](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-blob-storage)</span><span class="sxs-lookup"><span data-stu-id="d55dc-105">Read and write objects and files from [Azure Blob storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-blob-storage)</span></span>
- <span data-ttu-id="d55dc-106">Enviar e receber mensagens entre aplicativos conectados à nuvem com o [Armazenamento de Filas do Azure](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-queues)</span><span class="sxs-lookup"><span data-stu-id="d55dc-106">Send and receive messages between cloud-connected applications with [Azure Queue storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-queues)</span></span>
- <span data-ttu-id="d55dc-107">Ler e gravar dados estruturados grandes com o [Armazenamento de Tabelas do Azure](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-table-storage)</span><span class="sxs-lookup"><span data-stu-id="d55dc-107">Read and write large structured data with [Azure Table storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-table-storage)</span></span>

<span data-ttu-id="d55dc-108">Criar, atualizar e gerenciar contas de Armazenamento do Azure e consultar e regenerar chaves de acesso dos seus aplicativos Node.js com os módulos de gerenciamento.</span><span class="sxs-lookup"><span data-stu-id="d55dc-108">Create, update, and manage Azure Storage accounts and query and regenerate access keys from your Node.js apps with the management modules.</span></span>

## <a name="client-package"></a><span data-ttu-id="d55dc-109">Pacote de Cliente</span><span class="sxs-lookup"><span data-stu-id="d55dc-109">Client Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="d55dc-110">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="d55dc-110">Install the npm module</span></span>

<span data-ttu-id="d55dc-111">Instalar o módulo npm de cliente de armazenamento do Azure</span><span class="sxs-lookup"><span data-stu-id="d55dc-111">Install the Azure storage client npm module</span></span>

```bash
npm install azure-storage
```

### <a name="example"></a><span data-ttu-id="d55dc-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d55dc-112">Example</span></span>

<span data-ttu-id="d55dc-113">Este exemplo cria um contêiner de armazenamento e carrega um arquivo local `data.txt` para ele.</span><span class="sxs-lookup"><span data-stu-id="d55dc-113">This example create a storage container and uploads a local file `data.txt` to it.</span></span>

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

## <a name="management-package"></a><span data-ttu-id="d55dc-114">Pacote de Gerenciamento</span><span class="sxs-lookup"><span data-stu-id="d55dc-114">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="d55dc-115">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="d55dc-115">Install the npm module</span></span> 

<span data-ttu-id="d55dc-116">Instalar o módulo npm de gerenciamento de armazenamento do Azure</span><span class="sxs-lookup"><span data-stu-id="d55dc-116">Install the Azure storage management npm module</span></span>

```bash
npm install azure-arm-storage
```

### <a name="example"></a><span data-ttu-id="d55dc-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d55dc-117">Example</span></span>

<span data-ttu-id="d55dc-118">Este exemplo lista as contas de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="d55dc-118">This example list the storage accounts.</span></span>

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

## <a name="samples"></a><span data-ttu-id="d55dc-119">Exemplos</span><span class="sxs-lookup"><span data-stu-id="d55dc-119">Samples</span></span>

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/storage-samples.md)]

<span data-ttu-id="d55dc-120">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="d55dc-120">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
