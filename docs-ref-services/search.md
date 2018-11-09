---
title: Módulos do Azure Search para Node.js
description: Referência dos módulos do Azure Search para Node.js
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Search
ms.openlocfilehash: a9c34a57d7964de1713ebf4d6c0f9c000df33042
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/08/2018
ms.locfileid: "51173095"
---
# <a name="azure-search-modules-for-nodejs"></a><span data-ttu-id="e2bf4-103">Módulos do Azure Search para Node.js</span><span class="sxs-lookup"><span data-stu-id="e2bf4-103">Azure Search modules for Node.js</span></span>

<span data-ttu-id="e2bf4-104">O Azure Search é uma solução de pesquisa como um serviço de nuvem que delega o gerenciamento de infraestrutura e servidor à Microsoft, fornecendo um serviço pronto para uso que você pode preencher com seus dados e então utilizar para adicionar pesquisa a seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e2bf4-104">Azure Search is a cloud search-as-a-service solution that delegates server and infrastructure management to Microsoft, leaving you with a ready-to-use service that you can populate with your data and then use to add search to your application.</span></span>

<span data-ttu-id="e2bf4-105">Saiba mais sobre o [Azure Search](https://docs.microsoft.com/azure/search/search-what-is-azure-search).</span><span class="sxs-lookup"><span data-stu-id="e2bf4-105">Learn more about [Azure Search](https://docs.microsoft.com/azure/search/search-what-is-azure-search).</span></span>

## <a name="management-package"></a><span data-ttu-id="e2bf4-106">Pacote de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="e2bf4-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="e2bf4-107">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="e2bf4-107">Install the npm module</span></span>

<span data-ttu-id="e2bf4-108">Instalar o módulo npm do Azure Search</span><span class="sxs-lookup"><span data-stu-id="e2bf4-108">Install the Azure Search npm module</span></span>

```bash
npm install azure-arm-search
```

### <a name="example"></a><span data-ttu-id="e2bf4-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e2bf4-109">Example</span></span>

<span data-ttu-id="e2bf4-110">Este exemplo cria um novo serviço Search no Azure e lista os recursos em seus grupos de recursos.</span><span class="sxs-lookup"><span data-stu-id="e2bf4-110">This example creates a new Search service in Azure, and lists the resources in its resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="e2bf4-111">Exemplos</span><span class="sxs-lookup"><span data-stu-id="e2bf4-111">Samples</span></span>

<span data-ttu-id="e2bf4-112">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="e2bf4-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
