---
title: Módulos de Máquina Virtual para Node.js – Azure
description: Módulos de Máquina Virtual do Azure para guia de referência do Node.js
author: iainfoulds
ms.author: iainfou
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: compute
ms.openlocfilehash: 891b441d25369db0f0a67d791d527e6644415434
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34259838"
---
# <a name="azure-virtual-machine-modules-for-nodejs"></a><span data-ttu-id="d402f-103">Módulos de Máquina Virtual do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="d402f-103">Azure Virtual Machine Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="d402f-104">Visão geral</span><span class="sxs-lookup"><span data-stu-id="d402f-104">Overview</span></span>

<span data-ttu-id="d402f-105">Defina, configure e implante as novas máquinas virtuais do Windows e do Linux e os conjuntos de escalas de máquina virtual do seu código com os módulos de gerenciamento do Azure para Node.js.</span><span class="sxs-lookup"><span data-stu-id="d402f-105">Define, configure, and deploy new Windows and Linux virtual machines and virtual machine scale sets from your code with the Azure management modules for Node.js.</span></span> <span data-ttu-id="d402f-106">Os módulos permitem que você inicie e pare máquinas virtuais existentes e anexe ou desanexe discos às VMs paradas na sua assinatura do Azure.</span><span class="sxs-lookup"><span data-stu-id="d402f-106">The modules let you start and stop existing virtual machines and attach or detach disks to stopped VMs in your Azure subscription.</span></span>

## <a name="management-package"></a><span data-ttu-id="d402f-107">Pacote de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="d402f-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="d402f-108">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="d402f-108">Install the npm module</span></span>

<span data-ttu-id="d402f-109">Instalar o módulo npm da Computação do Azure</span><span class="sxs-lookup"><span data-stu-id="d402f-109">Install the Azure Compute npm module</span></span>

```bash
npm install azure-arm-compute
```   

### <a name="example"></a><span data-ttu-id="d402f-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d402f-110">Example</span></span>

<span data-ttu-id="d402f-111">O exemplo a seguir ilustra como fazer logon no Azure, criar um cliente de gerenciamento e listar todas as imagens de VM para o local, o publicador, a oferta e a SKU especificados.</span><span class="sxs-lookup"><span data-stu-id="d402f-111">The following example illustrates how to log in to Azure, create a management client, and list all VM images for the specified location, publisher, offer, and SKU.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const computeManagementClient = require('azure-arm-compute');

const subscriptionId = 'my-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new computeManagementClient(credentials, subscriptionId);

  client.virtualMachineImages
    .list(
        'westus',                   // location
        'Canonical',   // publisher name
        'UbuntuServer',            // offer
        '16.04-LTS'        // sku
    )
    .then(result => console.log(result));
});
```

## <a name="samples"></a><span data-ttu-id="d402f-112">Exemplos</span><span class="sxs-lookup"><span data-stu-id="d402f-112">Samples</span></span>

[!INCLUDE [node-virtualmachines-samples](../docs-ref-conceptual/includes/virtualmachines-samples.md)]

<span data-ttu-id="d402f-113">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="d402f-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
