---
title: "Módulos do Registro de Contêiner do Azure para Node.js"
description: "Referência dos módulos de Registro de Contêiner do Azure para Node.js"
keywords: "Azure, SDK, API, Registro de Contêiner, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Container Registry
ms.openlocfilehash: 6ded68c19971a8fe580f440862d0fe05a1def6a2
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-container-registry-modules-for-nodejs"></a><span data-ttu-id="d2d61-104">Módulos do Registro de Contêiner do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="d2d61-104">Azure Container Registry modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="d2d61-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="d2d61-105">Overview</span></span>

<span data-ttu-id="d2d61-106">O Registro de Contêiner do Azure é um serviço gerenciado do registro do Docker com base no Docker Registry 2.0 de software livre.</span><span class="sxs-lookup"><span data-stu-id="d2d61-106">Azure Container Registry is a managed Docker registry service based on the open-source Docker Registry 2.0.</span></span> <span data-ttu-id="d2d61-107">Criar e manter registros de contêiner do Azure para armazenar e gerenciar suas imagens privadas de contêiner Docker.</span><span class="sxs-lookup"><span data-stu-id="d2d61-107">Create and maintain Azure container registries to store and manage your private Docker container images.</span></span> <span data-ttu-id="d2d61-108">Use registros de contêiner no Azure com o desenvolvimento de contêiner e os pipelines de implantação existentes e tire proveito da experiência da comunidade do Docker.</span><span class="sxs-lookup"><span data-stu-id="d2d61-108">Use container registries in Azure with your existing container development and deployment pipelines, and draw on the body of Docker community expertise.</span></span>

## <a name="management-package"></a><span data-ttu-id="d2d61-109">Pacote de Gerenciamento</span><span class="sxs-lookup"><span data-stu-id="d2d61-109">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="d2d61-110">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="d2d61-110">Install the npm module</span></span>

<span data-ttu-id="d2d61-111">Instalar o módulo npm de registro de contêiner do Azure</span><span class="sxs-lookup"><span data-stu-id="d2d61-111">Install the Azure container registry npm module</span></span>

```bash
npm install azure-arm-containerregistry
```

### <a name="example"></a><span data-ttu-id="d2d61-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d2d61-112">Example</span></span>

<span data-ttu-id="d2d61-113">Este exemplo obtém uma lista de contêineres disponíveis.</span><span class="sxs-lookup"><span data-stu-id="d2d61-113">This example gets a list of the available containers.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const ContainerRegistryManagement = require('azure-arm-containerregistry');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const manager = new ContainerRegistryManagement(
      credentials,
      subscriptionId
    );
    return manager.registries.list();
  })
  .then(registries => {
    console.log('List of registries:');
    console.dir(registries, { depth: null, colors: true });
  });
```

## <a name="samples"></a><span data-ttu-id="d2d61-114">Exemplos</span><span class="sxs-lookup"><span data-stu-id="d2d61-114">Samples</span></span>

<span data-ttu-id="d2d61-115">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="d2d61-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
