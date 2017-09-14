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
# <a name="azure-virtual-machine-modules-for-nodejs"></a>Módulos de Máquina Virtual do Azure para Node.js

## <a name="overview"></a>Visão geral

Defina, configure e implante as novas máquinas virtuais do Windows e do Linux e os conjuntos de escalas de máquina virtual do seu código com os módulos de gerenciamento do Azure para Node.js. Os módulos permitem que você inicie e pare máquinas virtuais existentes e anexe ou desanexe discos às VMs paradas na sua assinatura do Azure.

## <a name="management-package"></a>Pacote de gerenciamento

### <a name="install-the-npm-module"></a>Instalar o módulo npm

Instalar o módulo npm da Computação do Azure

```bash
npm install azure-arm-compute
```   

### <a name="example"></a>Exemplo

O exemplo a seguir ilustra como fazer logon no Azure, criar um cliente de gerenciamento e listar todas as imagens de VM para o local, o publicador, a oferta e a SKU especificados.

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

## <a name="samples"></a>Exemplos

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/virtualmachines-samples.md)]

Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.
