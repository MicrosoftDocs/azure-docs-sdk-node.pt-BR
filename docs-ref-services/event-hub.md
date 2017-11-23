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
# <a name="azure-event-hub-modules-for-nodejs"></a><span data-ttu-id="a1f05-104">Módulos de Hub de Eventos do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="a1f05-104">Azure Event Hub modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="a1f05-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="a1f05-105">Overview</span></span>
<span data-ttu-id="a1f05-106">Os Hubs de Evento do Azure são um plataforma de transmissão de dados altamente dimensionável e um serviço de ingestão de dados capaz de receber e processar milhões de eventos por segundo.</span><span class="sxs-lookup"><span data-stu-id="a1f05-106">Azure Event Hubs is a highly scalable data streaming platform and event ingestion service capable of receiving and processing millions of events per second.</span></span> <span data-ttu-id="a1f05-107">Os Hubs de Eventos podem processar e armazenar eventos, dados ou telemetria produzidos pelos dispositivos e software distribuídos.</span><span class="sxs-lookup"><span data-stu-id="a1f05-107">Event Hubs can process and store events, data, or telemetry produced by distributed software and devices.</span></span> <span data-ttu-id="a1f05-108">Os dados enviados para um Hub de Eventos podem ser transformados e armazenados usando qualquer provedor de análise em tempo real ou adaptadores de envio em lote/armazenamento.</span><span class="sxs-lookup"><span data-stu-id="a1f05-108">Data sent to an event hub can be transformed and stored using any real-time analytics provider or batching/storage adapters.</span></span> <span data-ttu-id="a1f05-109">Com a capacidade de fornecer recursos de publicação/assinatura com baixa latência e em grande escala, os Hubs de Eventos servem como uma "subida" para Big Data.</span><span class="sxs-lookup"><span data-stu-id="a1f05-109">With the ability to provide publish-subscribe capabilities with low latency and at massive scale, Event Hubs serves as the "on ramp" for Big Data.</span></span>

## <a name="management-package"></a><span data-ttu-id="a1f05-110">Pacote de Gerenciamento</span><span class="sxs-lookup"><span data-stu-id="a1f05-110">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="a1f05-111">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="a1f05-111">Install the npm module</span></span> 

<span data-ttu-id="a1f05-112">Usar o npm para instalar os módulos do Hub de Eventos do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="a1f05-112">Use npm to install the Azure Event Hub modules for Node.js</span></span>

```bash
npm install azure-arm-eventhub
```

### <a name="example"></a><span data-ttu-id="a1f05-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a1f05-113">Example</span></span>

<span data-ttu-id="a1f05-114">Este exemplo recupera informações sobre um hub de eventos existente.</span><span class="sxs-lookup"><span data-stu-id="a1f05-114">This example retrieves information about an existing event hub.</span></span>

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

## <a name="samples"></a><span data-ttu-id="a1f05-115">Exemplos</span><span class="sxs-lookup"><span data-stu-id="a1f05-115">Samples</span></span>

<span data-ttu-id="a1f05-116">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="a1f05-116">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
