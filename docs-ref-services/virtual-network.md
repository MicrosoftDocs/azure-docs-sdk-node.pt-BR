---
title: "Módulos de Rede Virtual do Azure para Node.js"
description: "Referência dos módulos de Rede Virtual do Azure para Node.js"
keywords: Azure, SDK, API, Rede Virtual, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Virtual Network
ms.openlocfilehash: a17615a832c6dddeb7fef0a8a327dbf86ae281a7
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-virtual-network-modules-for-nodejs"></a><span data-ttu-id="93251-104">Módulos de Rede Virtual do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="93251-104">Azure Virtual Network modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="93251-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="93251-105">Overview</span></span>

<span data-ttu-id="93251-106">O serviço de Rede Virtual do Azure permite que você conecte com segurança os recursos do Azure usando redes virtuais (VNets).</span><span class="sxs-lookup"><span data-stu-id="93251-106">The Azure Virtual Network service enables you to securely connect Azure resources to each other with virtual networks (VNets).</span></span> <span data-ttu-id="93251-107">Uma VNet é uma representação da sua própria rede na nuvem.</span><span class="sxs-lookup"><span data-stu-id="93251-107">A VNet is a representation of your own network in the cloud.</span></span> <span data-ttu-id="93251-108">Uma VNet é um isolamento lógico da nuvem do Azure dedicada à sua assinatura.</span><span class="sxs-lookup"><span data-stu-id="93251-108">A VNet is a logical isolation of the Azure cloud dedicated to your subscription.</span></span> <span data-ttu-id="93251-109">Você também pode conectar VNets à sua rede local.</span><span class="sxs-lookup"><span data-stu-id="93251-109">You can also connect VNets to your on-premises network.</span></span>

<span data-ttu-id="93251-110">Saiba mais sobre a [Rede Virtual do Azure](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview).</span><span class="sxs-lookup"><span data-stu-id="93251-110">Learn more about [Azure Virtual Network](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="93251-111">Pacote de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="93251-111">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="93251-112">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="93251-112">Install the npm module</span></span>

<span data-ttu-id="93251-113">Instalar o módulo npm da Rede Virtual do Azure</span><span class="sxs-lookup"><span data-stu-id="93251-113">Install the Azure Virtual Network npm module</span></span>

```bash
npm install azure-arm-network
```

### <a name="example"></a><span data-ttu-id="93251-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="93251-114">Example</span></span>

<span data-ttu-id="93251-115">Este exemplo obtém e imprime a lista de redes virtuais</span><span class="sxs-lookup"><span data-stu-id="93251-115">This example gets and prints the list of virtual networks</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const NetworkManagementClient = require('azure-arm-network');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new NetworkManagementClient(credentials, subscriptionId);
    return client.virtualNetworks.list(resourceGroup);
  })
  .then(networkList => {
    console.log('List of virtual networks:');
    console.dir(networkList, { depth: null, colors: true });
  });

```

## <a name="samples"></a><span data-ttu-id="93251-116">Exemplos</span><span class="sxs-lookup"><span data-stu-id="93251-116">Samples</span></span>

<span data-ttu-id="93251-117">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="93251-117">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
