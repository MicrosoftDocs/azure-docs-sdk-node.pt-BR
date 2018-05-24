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
ms.openlocfilehash: 77dd4c30da43af7cace048b43b7997fb1952abf1
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="azure-iot-hub-modules-for-nodejs"></a>Módulos de Hub IoT do Azure para Node.js

O Hub IoT do Azure é um serviço totalmente gerenciado que permite comunicações bidirecionais confiáveis e seguras entre milhões de dispositivos IoT e um back-end da solução. Hub IoT do Azure:
- Fornece várias opções de comunicação do dispositivo para a nuvem e da nuvem para o dispositivo incluindo: mensagens unidirecionais, transferência de arquivos e métodos de solicitação de resposta.
- Fornece o roteamento de mensagens declarativas interno para outros serviços do Azure.
- Fornece um armazenamento consultável para metadados de dispositivo e informações de estado sincronizado.
- Habilita comunicações seguras e controle de acesso usando chaves de segurança por dispositivo ou certificados X.509.
- Fornece monitoramento abrangente para eventos de gerenciamento de identidade do dispositivo e de conectividade do dispositivo.
- Inclui bibliotecas de dispositivo para as plataformas e idiomas mais populares.

Use npm para instalar os módulos do Azure IoT Hub para Node.js

## <a name="management-package"></a>Pacote de Gerenciamento

### <a name="install-the-npm-module"></a>Instalar o módulo npm

Instalar o módulo npm do Hub IoT do Azure

```bash
npm install azure-arm-iothub
```

### <a name="example"></a>Exemplo

Este exemplo cria e nomeia um hub IoT.

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

Este exemplo obtém o hub IoT existente por nome.

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

## <a name="samples"></a>Exemplos

- [Introdução ao Kit de Início do Azure IoT Raspberry Pi](https://azure.microsoft.com/resources/samples/iot-remote-monitoring-node-raspberrypi-getstartedkit/)
- [Anomalias de vibração de tweet detectadas por serviços IoT do Azure em dados de um Intel Edison executando Node.js](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/)

Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.
