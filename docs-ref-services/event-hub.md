---
title: Módulos de Hub de Eventos do Azure para Node.js
description: Referência dos módulos do Hub de Eventos do Azure para Node.js
author: sethmanheim
ms.author: sethm
manager: timlt
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Event Hub
ms.openlocfilehash: ff167e911b68b82b880e792e7ff2649cbe5af342
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34260379"
---
# <a name="azure-event-hub-modules-for-nodejs"></a><span data-ttu-id="31f0b-103">Módulos de Hub de Eventos do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="31f0b-103">Azure Event Hub modules for Node.js</span></span>

<span data-ttu-id="31f0b-104">Os Hubs de Evento do Azure são um plataforma de transmissão de dados altamente dimensionável e um serviço de ingestão de dados capaz de receber e processar milhões de eventos por segundo.</span><span class="sxs-lookup"><span data-stu-id="31f0b-104">Azure Event Hubs is a highly scalable data streaming platform and event ingestion service capable of receiving and processing millions of events per second.</span></span> <span data-ttu-id="31f0b-105">Os Hubs de Eventos podem processar e armazenar eventos, dados ou telemetria produzidos pelos dispositivos e software distribuídos.</span><span class="sxs-lookup"><span data-stu-id="31f0b-105">Event Hubs can process and store events, data, or telemetry produced by distributed software and devices.</span></span> <span data-ttu-id="31f0b-106">Os dados enviados para um Hub de Eventos podem ser transformados e armazenados usando qualquer provedor de análise em tempo real ou adaptadores de envio em lote/armazenamento.</span><span class="sxs-lookup"><span data-stu-id="31f0b-106">Data sent to an event hub can be transformed and stored using any real-time analytics provider or batching/storage adapters.</span></span> <span data-ttu-id="31f0b-107">Com a capacidade de fornecer recursos de publicação/assinatura com baixa latência e em grande escala, os Hubs de Eventos servem como uma "subida" para Big Data.</span><span class="sxs-lookup"><span data-stu-id="31f0b-107">With the ability to provide publish-subscribe capabilities with low latency and at massive scale, Event Hubs serves as the "on ramp" for Big Data.</span></span>

## <a name="management-package"></a><span data-ttu-id="31f0b-108">Pacote de Gerenciamento</span><span class="sxs-lookup"><span data-stu-id="31f0b-108">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="31f0b-109">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="31f0b-109">Install the npm module</span></span> 

<span data-ttu-id="31f0b-110">Usar o npm para instalar os módulos do Hub de Eventos do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="31f0b-110">Use npm to install the Azure Event Hub modules for Node.js</span></span>

```bash
npm install azure-arm-eventhub
```

### <a name="example"></a><span data-ttu-id="31f0b-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="31f0b-111">Example</span></span>

<span data-ttu-id="31f0b-112">Este exemplo recupera informações sobre um hub de eventos existente.</span><span class="sxs-lookup"><span data-stu-id="31f0b-112">This example retrieves information about an existing event hub.</span></span>

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

## <a name="samples"></a><span data-ttu-id="31f0b-113">Exemplos</span><span class="sxs-lookup"><span data-stu-id="31f0b-113">Samples</span></span>

<span data-ttu-id="31f0b-114">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="31f0b-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
