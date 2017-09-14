---
title: "Módulos de Mapa do Serviço do Azure para Node.js"
description: "Referência dos módulos de Mapa do Serviço do Azure para Node.js"
keywords: "Azure, SDK, API, Mapa do Serviço, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Map
ms.openlocfilehash: 330cbceb07ba8bea65c1059a1edb3cd9c69653bc
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-service-map-modules-for-nodejs"></a>Módulos de Mapa do Serviço do Azure para Node.js

## <a name="overview"></a>Visão geral

O Mapa do Serviço detecta automaticamente os componentes de aplicativos em sistemas Windows e Linux e mapeia a comunicação entre os serviços. O Mapa do Serviço mostra conexões entre servidores, processos e portas em qualquer arquitetura conectada a TCP sem nenhuma configuração necessária além da instalação de um agente.

Saiba mais sobre o [Mapa do Serviço do Azure](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-service-map).

## <a name="management-package"></a>Pacote de gerenciamento

### <a name="install-the-npm-module"></a>Instalar o módulo npm

Instalar o módulo npm do Mapa do Serviço do Azure

```bash
npm install azure-arm-servicemap
```

### <a name="example"></a>Exemplo

Este exemplo lista todos os mapas de serviço para o grupo de recursos e o espaço de trabalho especificados.

```javascript
const msRestAzure = require('ms-rest-azure');
const serviceMapManagement = require('azure-arm-servicemap');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
const workspace = 'your-workspace';
let serviceMapClient;

msRestAzure.interactiveLogin().then(credentials => {
  serviceMapClient = new serviceMapManagement(credentials, subscriptionId);
  serviceMapClient.machineGroups
    .listByWorkspace(resourceGroup, workspace)
    .then(machineGroups => console.log('Retrieved machine groups: ', machineGroups));
});
```

## <a name="samples"></a>Exemplos

Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.
