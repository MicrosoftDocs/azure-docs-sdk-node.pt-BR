---
title: "Módulos de Barramento de Serviço do Azure para Node.js"
description: "Referência de módulos do Barramento de Serviço do Azure para Node.js"
keywords: "Azure, SDK, API, Barramento de Serviço, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Bus
ms.openlocfilehash: 4d1bbe917512d2ad5383081bef2c28a33541f28c
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-service-bus-modules-for-nodejs"></a>Módulos de Barramento de Serviço do Azure para Node.js

## <a name="overview"></a>Visão geral

O Barramento de Serviço do Azure é uma plataforma de nuvem de mensagens assíncronas que permite enviar dados entre sistemas separados.

Saiba mais sobre o [Barramento de Serviço do Azure](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview).

## <a name="management-package"></a>Pacote de gerenciamento

### <a name="install-the-npm-module"></a>Instalar o módulo npm

Use npm para instalar o módulo do Barramento de Serviço do Azure para Node.js

```bash
npm install azure-arm-sb
```

### <a name="example"></a>Exemplo

Este exemplo cria um cliente e, em seguida, lista todos os namespaces do Barramento de Serviço associados a uma determinada assinatura.

```javascript
const msRestAzure = require('ms-rest-azure');
const ServicebusManagement = require('azure-arm-sb');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
    const client = new ServicebusManagement(credentials, subscriptionId);
    client.namespaces.listBySubscription().then(namespaces => {
        namespaces.map(ns => {
            console.log(`found ns : ${ns.name}`);
        });
    });
});
```

## <a name="samples"></a>Exemplos

Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.
