---
title: "Módulos de Hubs de Notificação do Azure para Node.js"
description: "Referência dos módulos de Hubs de Notificação do Azure para Node.js"
keywords: "Azure, SDK, API, Hubs de Notificação, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Notification Hubs
ms.openlocfilehash: 0141760cb93c77faed4a04893fe1376e4e75c361
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-notification-hubs-modules-for-nodejs"></a>Módulos de Hubs de Notificação do Azure para Node.js

## <a name="overview"></a>Visão geral

Os Hubs de Notificação do Azure fornecem um mecanismo de envio por push fácil de usar, multiplataforma e dimensionável. Com uma chamada à API única entre plataformas, você pode enviar notificações por push direcionadas e personalizadas para qualquer plataforma móvel de qualquer back-end local ou em nuvem.

Os Hubs de Notificação funcionam bem tanto para cenários empresariais quanto para cenários de consumidor. Aqui temos alguns exemplos de como os consumidores usam os Hubs de Notificação:
- Para enviar notificações sobre as novidades para milhões de pessoas com baixa latência.
- Para enviar cupons baseados na localização para segmentos de usuários interessados.
- Para enviar notificações de eventos para usuários ou grupos em aplicativos de mídia/esportes/finanças/jogos.
- Para enviar por push conteúdos promocionais para aplicativos com o objetivo de atrair e vender para os clientes.
- Para notificar os usuários sobre eventos corporativos, como novas mensagens e itens de trabalho.
- Para enviar códigos para Autenticação Multifator.

## <a name="management-package"></a>Pacote de Gerenciamento

### <a name="install-the-npm-module"></a>Instalar o módulo npm

Instalar o módulo de Hubs de Notificação do Azure 

```bash
npm install azure-arm-notificationhubs
```

### <a name="example"></a>Exemplo

Este exemplo lista todos os hubs de notificação.

 ```javascript
const msRestAzure = require('ms-rest-azure');
const notificationHubsManagementClient = require('azure-arm-notificationhubs');

const subscriptionId = 'your-subscription-id';
const notificationHubNamespace = 'your-hub-namespace';
const resourceGroup = 'your-resource-group';
let notificationHubsClient;

msRestAzure.interactiveLogin().then(credentials => {
  notificationHubsClient = new notificationHubsManagementClient(credentials, subscriptionId);
  notificationHubsClient.notificationHubs
    .list(resourceGroup, notificationHubNamespace)
    .then(notificationHubs => console.log('Retrieved notification hubs: ', notificationHubs));
});
```

## <a name="samples"></a>Exemplos

* [Início rápido concluído para Aplicativo Móvel do Serviço de Aplicativo para back-end do Node.js](https://azure.microsoft.com/resources/samples/app-service-mobile-nodejs-backend-quickstart/)
* [Anomalias de vibração de tweet detectadas por serviços IoT do Azure em dados de um Intel Edison executando Node.js](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/)

Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.
