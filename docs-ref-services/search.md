---
title: "Módulos do Azure Search para Node.js"
description: "Referência dos módulos do Azure Search para Node.js"
keywords: Azure, SDK, API, Search, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Search
ms.openlocfilehash: dc9d4c5128c99a9518bd059e191bb11e4de4b78f
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-search-modules-for-nodejs"></a><span data-ttu-id="00def-104">Módulos do Azure Search para Node.js</span><span class="sxs-lookup"><span data-stu-id="00def-104">Azure Search modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="00def-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="00def-105">Overview</span></span>

<span data-ttu-id="00def-106">O Azure Search é uma solução de pesquisa como um serviço de nuvem que delega o gerenciamento de infraestrutura e servidor à Microsoft, fornecendo um serviço pronto para uso que você pode preencher com seus dados e então utilizar para adicionar pesquisa a seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="00def-106">Azure Search is a cloud search-as-a-service solution that delegates server and infrastructure management to Microsoft, leaving you with a ready-to-use service that you can populate with your data and then use to add search to your application.</span></span>

<span data-ttu-id="00def-107">Saiba mais sobre o [Azure Search](https://docs.microsoft.com/azure/search/search-what-is-azure-search).</span><span class="sxs-lookup"><span data-stu-id="00def-107">Learn more about [Azure Search](https://docs.microsoft.com/azure/search/search-what-is-azure-search).</span></span>

## <a name="management-package"></a><span data-ttu-id="00def-108">Pacote de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="00def-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="00def-109">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="00def-109">Install the npm module</span></span>

<span data-ttu-id="00def-110">Instalar o módulo npm do Azure Search</span><span class="sxs-lookup"><span data-stu-id="00def-110">Install the Azure Search npm module</span></span>

```bash
npm install azure-arm-search
```

### <a name="example"></a><span data-ttu-id="00def-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="00def-111">Example</span></span>

<span data-ttu-id="00def-112">Este exemplo cria um novo serviço Search no Azure e lista os recursos em seus grupos de recursos.</span><span class="sxs-lookup"><span data-stu-id="00def-112">This example creates a new Search service in Azure, and lists the resources in its resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const SearchManagement = require('azure-arm-search');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'yourResourceGroup';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new SearchManagement(credentials, subscriptionId);
    return client.services.listByResourceGroup(resourceGroup);
  })
  .then(services => console.dir(services, { depth: null, colors: true }))
  .catch(err => {
    console.log('An error ocurred');
    console.dir(err, { depth: null, colors: true });
  });
```

## <a name="samples"></a><span data-ttu-id="00def-113">Exemplos</span><span class="sxs-lookup"><span data-stu-id="00def-113">Samples</span></span>

<span data-ttu-id="00def-114">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="00def-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
