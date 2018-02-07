---
title: "Módulos de Máquina Virtual para Node.js – Azure"
description: "Módulos de Máquina Virtual do Azure para guia de referência do Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: compute
ms.openlocfilehash: 608a915499d7c32c2c8b04464f716fa4fd17243d
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/26/2018
---
# <a name="azure-virtual-machine-modules-for-nodejs"></a><span data-ttu-id="d047c-103">Módulos de Máquina Virtual do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="d047c-103">Azure Virtual Machine Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="d047c-104">Visão geral</span><span class="sxs-lookup"><span data-stu-id="d047c-104">Overview</span></span>

<span data-ttu-id="d047c-105">Defina, configure e implante as novas máquinas virtuais do Windows e do Linux e os conjuntos de escalas de máquina virtual do seu código com os módulos de gerenciamento do Azure para Node.js.</span><span class="sxs-lookup"><span data-stu-id="d047c-105">Define, configure, and deploy new Windows and Linux virtual machines and virtual machine scale sets from your code with the Azure management modules for Node.js.</span></span> <span data-ttu-id="d047c-106">Os módulos permitem que você inicie e pare máquinas virtuais existentes e anexe ou desanexe discos às VMs paradas na sua assinatura do Azure.</span><span class="sxs-lookup"><span data-stu-id="d047c-106">The modules let you start and stop existing virtual machines and attach or detach disks to stopped VMs in your Azure subscription.</span></span>

## <a name="management-package"></a><span data-ttu-id="d047c-107">Pacote de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="d047c-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="d047c-108">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="d047c-108">Install the npm module</span></span>

<span data-ttu-id="d047c-109">Instalar o módulo npm da Computação do Azure</span><span class="sxs-lookup"><span data-stu-id="d047c-109">Install the Azure Compute npm module</span></span>

```bash
npm install azure-arm-compute
```   

### <a name="example"></a><span data-ttu-id="d047c-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d047c-110">Example</span></span>

<span data-ttu-id="d047c-111">O exemplo a seguir ilustra como fazer logon no Azure, criar um cliente de gerenciamento e listar todas as imagens de VM para o local, o publicador, a oferta e a SKU especificados.</span><span class="sxs-lookup"><span data-stu-id="d047c-111">The following example illustrates how to log in to Azure, create a management client, and list all VM images for the specified location, publisher, offer, and SKU.</span></span>

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

## <a name="samples"></a><span data-ttu-id="d047c-112">Exemplos</span><span class="sxs-lookup"><span data-stu-id="d047c-112">Samples</span></span>

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/virtualmachines-samples.md)]

<span data-ttu-id="d047c-113">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="d047c-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
