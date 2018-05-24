---
title: Módulos de Barramento de Serviço do Azure para Node.js
description: Referência de módulos do Barramento de Serviço do Azure para Node.js
author: sethmanheim
ms.author: sethm
manager: timlt
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Bus
ms.openlocfilehash: fde02006fcf364071fcb866098dba7fcd3b1c07b
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="azure-service-bus-modules-for-nodejs"></a><span data-ttu-id="79e94-103">Módulos de Barramento de Serviço do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="79e94-103">Azure Service Bus Modules for Node.js</span></span>

<span data-ttu-id="79e94-104">O Barramento de Serviço do Azure é uma plataforma de nuvem de mensagens assíncronas que permite enviar dados entre sistemas separados.</span><span class="sxs-lookup"><span data-stu-id="79e94-104">Azure Service Bus is an asynchronous messaging cloud platform that enables you to send data between decoupled systems.</span></span>

<span data-ttu-id="79e94-105">Saiba mais sobre o [Barramento de Serviço do Azure](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview).</span><span class="sxs-lookup"><span data-stu-id="79e94-105">Learn more about [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="79e94-106">Pacote de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="79e94-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="79e94-107">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="79e94-107">Install the npm module</span></span>

<span data-ttu-id="79e94-108">Use npm para instalar o módulo do Barramento de Serviço do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="79e94-108">Use npm to install the Azure Service Bus module for Node.js</span></span>

```bash
npm install azure-arm-sb
```

### <a name="example"></a><span data-ttu-id="79e94-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="79e94-109">Example</span></span>

<span data-ttu-id="79e94-110">Este exemplo cria um cliente e, em seguida, lista todos os namespaces do Barramento de Serviço associados a uma determinada assinatura.</span><span class="sxs-lookup"><span data-stu-id="79e94-110">This example creates a client and then lists all Service Bus namespaces associated with a given subscription.</span></span>

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

## <a name="samples"></a><span data-ttu-id="79e94-111">Exemplos</span><span class="sxs-lookup"><span data-stu-id="79e94-111">Samples</span></span>

<span data-ttu-id="79e94-112">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="79e94-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
