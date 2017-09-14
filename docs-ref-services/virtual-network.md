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
# <a name="azure-virtual-network-modules-for-nodejs"></a>Módulos de Rede Virtual do Azure para Node.js

## <a name="overview"></a>Visão geral

O serviço de Rede Virtual do Azure permite que você conecte com segurança os recursos do Azure usando redes virtuais (VNets). Uma VNet é uma representação da sua própria rede na nuvem. Uma VNet é um isolamento lógico da nuvem do Azure dedicada à sua assinatura. Você também pode conectar VNets à sua rede local.

Saiba mais sobre a [Rede Virtual do Azure](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview).

## <a name="management-package"></a>Pacote de gerenciamento

### <a name="install-the-npm-module"></a>Instalar o módulo npm

Instalar o módulo npm da Rede Virtual do Azure

```bash
npm install azure-arm-network
```

### <a name="example"></a>Exemplo

Este exemplo obtém e imprime a lista de redes virtuais

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

## <a name="samples"></a>Exemplos

Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.
