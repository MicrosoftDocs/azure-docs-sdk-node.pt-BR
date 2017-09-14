---
title: "Módulos de Máquina Virtual do Azure para Node.js"
description: "Referência dos módulos de Máquina Virtual do Azure para Node.js"
keywords: "Azure, Node, SDK, API, máquina virtual, vm, nodejs, javascript"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: compute
ms.openlocfilehash: 816714f5c286ee82f61502978c5d811e9f283432
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-virtual-machine-modules-for-nodejs"></a><span data-ttu-id="06ef4-104">Módulos de Máquina Virtual do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="06ef4-104">Azure Virtual Machine Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="06ef4-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="06ef4-105">Overview</span></span>

<span data-ttu-id="06ef4-106">Defina, configure e implante as novas máquinas virtuais do Windows e do Linux e os conjuntos de escalas de máquina virtual do seu código com os módulos de gerenciamento do Azure para Node.js.</span><span class="sxs-lookup"><span data-stu-id="06ef4-106">Define, configure, and deploy new Windows and Linux virtual machines and virtual machine scale sets from your code with the Azure management modules for Node.js.</span></span> <span data-ttu-id="06ef4-107">Os módulos permitem que você inicie e pare máquinas virtuais existentes e anexe ou desanexe discos às VMs paradas na sua assinatura do Azure.</span><span class="sxs-lookup"><span data-stu-id="06ef4-107">The modules let you start and stop existing virtual machines and attach or detach disks to stopped VMs in your Azure subscription.</span></span>

## <a name="management-package"></a><span data-ttu-id="06ef4-108">Pacote de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="06ef4-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="06ef4-109">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="06ef4-109">Install the npm module</span></span>

<span data-ttu-id="06ef4-110">Instalar o módulo npm da Computação do Azure</span><span class="sxs-lookup"><span data-stu-id="06ef4-110">Install the Azure Compute npm module</span></span>

```bash
npm install azure-arm-compute
```   

### <a name="example"></a><span data-ttu-id="06ef4-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="06ef4-111">Example</span></span>

<span data-ttu-id="06ef4-112">O exemplo a seguir ilustra como fazer logon no Azure, criar um cliente de gerenciamento e listar todas as imagens de VM para o local, o publicador, a oferta e a SKU especificados.</span><span class="sxs-lookup"><span data-stu-id="06ef4-112">The following example illustrates how to log in to Azure, create a management client, and list all VM images for the specified location, publisher, offer, and SKU.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const computeManagementClient = require('azure-arm-compute');

const subscriptionId = 'my-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new computeManagementClient(credentials, subscriptionId);

  client.virtualMachineImages
    .list(
        'westus',                   // location
        'MicrosoftWindowsServer',   // publisher name
        'WindowsServer',            // offer
        '2012-R2-Datacenter'        // sku
    )
    .then(result => console.log(result));
});
```

## <a name="samples"></a><span data-ttu-id="06ef4-113">Exemplos</span><span class="sxs-lookup"><span data-stu-id="06ef4-113">Samples</span></span>

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/virtualmachines-samples.md)]

<span data-ttu-id="06ef4-114">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="06ef4-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
