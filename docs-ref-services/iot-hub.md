---
title: "Módulos de Hub IoT do Azure para Node.js"
description: "Referência dos módulos do Azure IoT Hub para Node.js"
keywords: Azure, SDK, API, Hub IoT, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: IoT Hub
ms.openlocfilehash: 44d01ceb833d2acbef6f9f22b32d4ad66b1fd5ec
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-iot-hub-modules-for-nodejs"></a><span data-ttu-id="0ab15-104">Módulos de Hub IoT do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="0ab15-104">Azure IoT Hub modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="0ab15-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="0ab15-105">Overview</span></span>

<span data-ttu-id="0ab15-106">O Hub IoT do Azure é um serviço totalmente gerenciado que permite comunicações bidirecionais confiáveis e seguras entre milhões de dispositivos IoT e um back-end da solução.</span><span class="sxs-lookup"><span data-stu-id="0ab15-106">Azure IoT Hub is a fully managed service that enables reliable and secure bidirectional communications between millions of IoT devices and a solution back end.</span></span> <span data-ttu-id="0ab15-107">Hub IoT do Azure:</span><span class="sxs-lookup"><span data-stu-id="0ab15-107">Azure IoT Hub:</span></span>
- <span data-ttu-id="0ab15-108">Fornece várias opções de comunicação do dispositivo para a nuvem e da nuvem para o dispositivo incluindo: mensagens unidirecionais, transferência de arquivos e métodos de solicitação de resposta.</span><span class="sxs-lookup"><span data-stu-id="0ab15-108">Provides multiple device-to-cloud and cloud-to-device communication options, including one-way messaging, file transfer, and request-reply methods.</span></span>
- <span data-ttu-id="0ab15-109">Fornece o roteamento de mensagens declarativas interno para outros serviços do Azure.</span><span class="sxs-lookup"><span data-stu-id="0ab15-109">Provides built-in declarative message routing to other Azure services.</span></span>
- <span data-ttu-id="0ab15-110">Fornece um armazenamento consultável para metadados de dispositivo e informações de estado sincronizado.</span><span class="sxs-lookup"><span data-stu-id="0ab15-110">Provides a queryable store for device metadata and synchronized state information.</span></span>
- <span data-ttu-id="0ab15-111">Habilita comunicações seguras e controle de acesso usando chaves de segurança por dispositivo ou certificados X.509.</span><span class="sxs-lookup"><span data-stu-id="0ab15-111">Enables secure communications and access control using per-device security keys or X.509 certificates.</span></span>
- <span data-ttu-id="0ab15-112">Fornece monitoramento abrangente para eventos de gerenciamento de identidade do dispositivo e de conectividade do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="0ab15-112">Provides extensive monitoring for device connectivity and device identity management events.</span></span>
- <span data-ttu-id="0ab15-113">Inclui bibliotecas de dispositivo para as plataformas e idiomas mais populares.</span><span class="sxs-lookup"><span data-stu-id="0ab15-113">Includes device libraries for the most popular languages and platforms.</span></span>

<span data-ttu-id="0ab15-114">Use npm para instalar os módulos do Azure IoT Hub para Node.js</span><span class="sxs-lookup"><span data-stu-id="0ab15-114">Use npm to install the Azure IoT Hub modules for Node.js</span></span>

## <a name="management-package"></a><span data-ttu-id="0ab15-115">Pacote de Gerenciamento</span><span class="sxs-lookup"><span data-stu-id="0ab15-115">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="0ab15-116">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="0ab15-116">Install the npm module</span></span>

<span data-ttu-id="0ab15-117">Instalar o módulo npm do Hub IoT do Azure</span><span class="sxs-lookup"><span data-stu-id="0ab15-117">Install the Azure IoT Hub npm module</span></span>

```bash
npm install azure-arm-iothub
```

### <a name="example"></a><span data-ttu-id="0ab15-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ab15-118">Example</span></span>

<span data-ttu-id="0ab15-119">Este exemplo cria e nomeia um hub IoT.</span><span class="sxs-lookup"><span data-stu-id="0ab15-119">This example creates and names an IoT hub.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const IoTHubClient = require('azure-arm-iothub');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
const hubName = 'your-hub';
const location = 'East US';

// Describe the IoT hub you want to create
const hubDescription = {
  name: hubName,
  location: location,
  subscriptionid: subscriptionId,
  resourcegroup: resourceGroup,
  sku: { name: 'S1', capacity: 2 },
  properties: {
    enableFileUploadNotifications: false,
    ipFilterRules: [{ filterName: 'ipfilterrule', action: 'accept', ipMask: '0.0.0.0/0' }],
    operationsMonitoringProperties: {
      events: {
        C2DCommands: 'Error',
        DeviceTelemetry: 'Error',
        DeviceIdentityOperations: 'Error',
        Connections: 'Error, Information'
      }
    },
    features: 'None'
  }
};

msRestAzure.interactiveLogin().then(credentials => {
  const client = new IoTHubClient(credentials, subscriptionId);

  client.iotHubResource
    .createOrUpdate(resourceGroup, hubName, hubDescription)
    .then(hubDescriptionResult => console.log(hubDescriptionResult))
    .catch(err => console.error(err));
});
```

<span data-ttu-id="0ab15-120">Este exemplo obtém o hub IoT existente por nome.</span><span class="sxs-lookup"><span data-stu-id="0ab15-120">This example gets the existing IoT hub, by name.</span></span>

```javascript
const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
const hubName = 'your-hub';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new IoTHubClient(credentials, subscriptionId);

  client.iotHubResource
    .get(resourceGroup, hubName)
    .then(hubDescriptionResult => console.log(hubDescriptionResult))
    .catch(err => console.error(err));
});
```

## <a name="samples"></a><span data-ttu-id="0ab15-121">Exemplos</span><span class="sxs-lookup"><span data-stu-id="0ab15-121">Samples</span></span>

- [<span data-ttu-id="0ab15-122">Introdução ao Kit de Início do Azure IoT Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="0ab15-122">Get started with the Raspberry Pi Azure IoT Starter Kit</span></span>](https://azure.microsoft.com/resources/samples/iot-remote-monitoring-node-raspberrypi-getstartedkit/)
- [<span data-ttu-id="0ab15-123">Anomalias de vibração de tweet detectadas por serviços IoT do Azure em dados de um Intel Edison executando Node.js</span><span class="sxs-lookup"><span data-stu-id="0ab15-123">Tweet vibration anomalies detected by Azure IoT services on data from an Intel Edison running Node.js</span></span>](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/)

<span data-ttu-id="0ab15-124">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="0ab15-124">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
