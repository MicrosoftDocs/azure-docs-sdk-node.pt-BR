---
title: Módulos de Hub IoT do Azure para Node.js
description: Referência dos módulos do Azure IoT Hub para Node.js
author: dominicbetts
ms.author: dobett
manager: timlt
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: IoT Hub
ms.openlocfilehash: 1f83e016023722f149384ac015726e9257a9f3af
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2018
ms.locfileid: "50326613"
---
# <a name="azure-iot-hub-modules-for-nodejs"></a><span data-ttu-id="9223a-103">Módulos de Hub IoT do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="9223a-103">Azure IoT Hub modules for Node.js</span></span>

<span data-ttu-id="9223a-104">O Hub IoT do Azure é um serviço totalmente gerenciado que permite comunicações bidirecionais confiáveis e seguras entre milhões de dispositivos IoT e um back-end da solução.</span><span class="sxs-lookup"><span data-stu-id="9223a-104">Azure IoT Hub is a fully managed service that enables reliable and secure bidirectional communications between millions of IoT devices and a solution back end.</span></span> <span data-ttu-id="9223a-105">Hub IoT do Azure:</span><span class="sxs-lookup"><span data-stu-id="9223a-105">Azure IoT Hub:</span></span>
- <span data-ttu-id="9223a-106">Fornece várias opções de comunicação do dispositivo para a nuvem e da nuvem para o dispositivo incluindo: mensagens unidirecionais, transferência de arquivos e métodos de solicitação de resposta.</span><span class="sxs-lookup"><span data-stu-id="9223a-106">Provides multiple device-to-cloud and cloud-to-device communication options, including one-way messaging, file transfer, and request-reply methods.</span></span>
- <span data-ttu-id="9223a-107">Fornece o roteamento de mensagens declarativas interno para outros serviços do Azure.</span><span class="sxs-lookup"><span data-stu-id="9223a-107">Provides built-in declarative message routing to other Azure services.</span></span>
- <span data-ttu-id="9223a-108">Fornece um armazenamento consultável para metadados de dispositivo e informações de estado sincronizado.</span><span class="sxs-lookup"><span data-stu-id="9223a-108">Provides a queryable store for device metadata and synchronized state information.</span></span>
- <span data-ttu-id="9223a-109">Habilita comunicações seguras e controle de acesso usando chaves de segurança por dispositivo ou certificados X.509.</span><span class="sxs-lookup"><span data-stu-id="9223a-109">Enables secure communications and access control using per-device security keys or X.509 certificates.</span></span>
- <span data-ttu-id="9223a-110">Fornece monitoramento abrangente para eventos de gerenciamento de identidade do dispositivo e de conectividade do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="9223a-110">Provides extensive monitoring for device connectivity and device identity management events.</span></span>
- <span data-ttu-id="9223a-111">Inclui bibliotecas de dispositivo para as plataformas e idiomas mais populares.</span><span class="sxs-lookup"><span data-stu-id="9223a-111">Includes device libraries for the most popular languages and platforms.</span></span>

<span data-ttu-id="9223a-112">Use npm para instalar os módulos do Azure IoT Hub para Node.js</span><span class="sxs-lookup"><span data-stu-id="9223a-112">Use npm to install the Azure IoT Hub modules for Node.js</span></span>

## <a name="management-package"></a><span data-ttu-id="9223a-113">Pacote de Gerenciamento</span><span class="sxs-lookup"><span data-stu-id="9223a-113">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="9223a-114">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="9223a-114">Install the npm module</span></span>

<span data-ttu-id="9223a-115">Instalar o módulo npm do Hub IoT do Azure</span><span class="sxs-lookup"><span data-stu-id="9223a-115">Install the Azure IoT Hub npm module</span></span>

```bash
npm install azure-arm-iothub
```

### <a name="example"></a><span data-ttu-id="9223a-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9223a-116">Example</span></span>

<span data-ttu-id="9223a-117">Este exemplo cria e nomeia um hub IoT.</span><span class="sxs-lookup"><span data-stu-id="9223a-117">This example creates and names an IoT hub.</span></span>

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

<span data-ttu-id="9223a-118">Este exemplo obtém o hub IoT existente por nome.</span><span class="sxs-lookup"><span data-stu-id="9223a-118">This example gets the existing IoT hub, by name.</span></span>

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

## <a name="samples"></a><span data-ttu-id="9223a-119">Exemplos</span><span class="sxs-lookup"><span data-stu-id="9223a-119">Samples</span></span>

- [<span data-ttu-id="9223a-120">Introdução ao Kit de Início do Azure IoT Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="9223a-120">Get started with the Raspberry Pi Azure IoT Starter Kit</span></span>](https://azure.microsoft.com/resources/samples/iot-remote-monitoring-node-raspberrypi-getstartedkit/)
- [<span data-ttu-id="9223a-121">Anomalias de vibração de tweet detectadas por serviços IoT do Azure em dados de um Intel Edison executando Node.js</span><span class="sxs-lookup"><span data-stu-id="9223a-121">Tweet vibration anomalies detected by Azure IoT services on data from an Intel Edison running Node.js</span></span>](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/)

<span data-ttu-id="9223a-122">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="9223a-122">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
