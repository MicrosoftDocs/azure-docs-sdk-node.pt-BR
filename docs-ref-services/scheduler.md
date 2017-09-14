---
title: "Módulos de Agendador do Azure para Node.js"
description: "Referência dos módulos de Agendador do Azure para Node.js"
keywords: Azure, SDK, API, Agendador, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Scheduler
ms.openlocfilehash: 3070612721dc434b8c3d7c3200f0666755fd4ce8
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-scheduler-modules-for-nodejs"></a>Módulos de Agendador do Azure para Node.js

## <a name="overview"></a>Visão geral

O Agendador do Azure cria, mantém e invoca o trabalho agendado por meio de HTTP, HTTPS, uma fila de armazenamento ou do [Barramento de Serviço do Azure](/azure/service-bus-messaging/service-bus-messaging-overview).

Saiba mais sobre o [Agendador do Azure](/azure/scheduler/scheduler-intro).

## <a name="management-package"></a>Pacote de gerenciamento

Crie, mantenha e invoque o trabalho agendado em vários canais de comunicação com a API de gerenciamento.

### <a name="install-the-npm-module"></a>Instalar o módulo npm

Instalar o módulo npm de Agendador do Azure

```bash
npm install azure-arm-scheduler
```

### <a name="example"></a>Exemplo

Este exemplo lista os agendadores atuais.

```javascript
const msRestAzure = require('ms-rest-azure')
const SchedulerManagement = require('azure-arm-scheduler')

msRestAzure.interactiveLogin().then(credentials => {
    // Create a scheduler from the login credentials
    let client = new SchedulerManagement(credentials, 'your-subscription-id')
    // Get the full list of current jobs for the subscription
    return client.jobCollections.listBySubscription()
}).then(currentJobs => {
    console.log("Current jobs:")
    console.dir(currentJobs, {depth:null, colors:true})
}).catch(error => {
    console.log("An error occurred:")
    console.dir(error, {depth:null, colors:true})
})
```

## <a name="samples"></a>Exemplos

Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.
