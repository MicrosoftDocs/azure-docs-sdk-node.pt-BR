---
title: Módulos do Registro de Contêiner do Azure para Node.js
description: Referência dos módulos de Registro de Contêiner do Azure para Node.js
author: mmacy
ms.author: marsma
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Container Registry
ms.openlocfilehash: f24fa268f9c471925a1bdf0cbae8044d97bc7679
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51477920"
---
# <a name="azure-container-registry-modules-for-nodejs"></a><span data-ttu-id="5c3db-103">Módulos do Registro de Contêiner do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="5c3db-103">Azure Container Registry modules for Node.js</span></span>

<span data-ttu-id="5c3db-104">O Registro de Contêiner do Azure é um serviço gerenciado do registro do Docker com base no Docker Registry 2.0 de software livre.</span><span class="sxs-lookup"><span data-stu-id="5c3db-104">Azure Container Registry is a managed Docker registry service based on the open-source Docker Registry 2.0.</span></span> <span data-ttu-id="5c3db-105">Criar e manter registros de contêiner do Azure para armazenar e gerenciar suas imagens privadas de contêiner Docker.</span><span class="sxs-lookup"><span data-stu-id="5c3db-105">Create and maintain Azure container registries to store and manage your private Docker container images.</span></span> <span data-ttu-id="5c3db-106">Use registros de contêiner no Azure com o desenvolvimento de contêiner e os pipelines de implantação existentes e tire proveito da experiência da comunidade do Docker.</span><span class="sxs-lookup"><span data-stu-id="5c3db-106">Use container registries in Azure with your existing container development and deployment pipelines, and draw on the body of Docker community expertise.</span></span>

## <a name="management-package"></a><span data-ttu-id="5c3db-107">Pacote de Gerenciamento</span><span class="sxs-lookup"><span data-stu-id="5c3db-107">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="5c3db-108">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="5c3db-108">Install the npm module</span></span>

<span data-ttu-id="5c3db-109">Instalar o módulo npm de registro de contêiner do Azure</span><span class="sxs-lookup"><span data-stu-id="5c3db-109">Install the Azure container registry npm module</span></span>

```bash
npm install azure-arm-containerregistry
```

### <a name="example"></a><span data-ttu-id="5c3db-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5c3db-110">Example</span></span>

<span data-ttu-id="5c3db-111">Este exemplo obtém uma lista de contêineres disponíveis.</span><span class="sxs-lookup"><span data-stu-id="5c3db-111">This example gets a list of the available containers.</span></span>

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

## <a name="samples"></a><span data-ttu-id="5c3db-112">Exemplos</span><span class="sxs-lookup"><span data-stu-id="5c3db-112">Samples</span></span>

<span data-ttu-id="5c3db-113">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="5c3db-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
