---
title: "Módulos de Hub de Eventos do Azure para Node.js"
description: "Referência dos módulos do Hub de Eventos do Azure para Node.js"
keywords: Azure, SDK, API, Hub de Eventos, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Event Hub
ms.openlocfilehash: 5ac6fc3f86419602756c354393078b399a6cba23
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-event-hub-modules-for-nodejs"></a>Módulos de Hub de Eventos do Azure para Node.js

## <a name="overview"></a>Visão geral
Os Hubs de Evento do Azure são um plataforma de transmissão de dados altamente dimensionável e um serviço de ingestão de dados capaz de receber e processar milhões de eventos por segundo. Os Hubs de Eventos podem processar e armazenar eventos, dados ou telemetria produzidos pelos dispositivos e software distribuídos. Os dados enviados para um Hub de Eventos podem ser transformados e armazenados usando qualquer provedor de análise em tempo real ou adaptadores de envio em lote/armazenamento. Com a capacidade de fornecer recursos de publicação/assinatura com baixa latência e em grande escala, os Hubs de Eventos servem como uma "subida" para Big Data.

## <a name="management-package"></a>Pacote de Gerenciamento

### <a name="install-the-npm-module"></a>Instalar o módulo npm 

Usar o npm para instalar os módulos do Hub de Eventos do Azure para Node.js

```bash
npm install azure-arm-eventhub
```

### <a name="example"></a>Exemplo

Este exemplo recupera informações sobre um hub de eventos existente.

```javascript
const msRestAzure = require('ms-rest-azure');
const EventHubManagement = require('azure-arm-eventhub');

const resourceGroupName = 'testRG';
const namespaceName = 'testNS';
const eventHubName = 'testEH';
const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new EventHubManagement(credentials, subscriptionId);
    return client.eventHubs.get(resourceGroupName, namespaceName, eventHubName);
  })
  .then(zones => console.dir(zones, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a>Exemplos

Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.
