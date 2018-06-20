---
title: Módulos de Agendador do Azure para Node.js
description: Referência dos módulos de Agendador do Azure para Node.js
author: rloutlaw
ms.author: ROutlaw
manager: angrobe
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Scheduler
ms.openlocfilehash: d52a61a786a86b21bc48752e6531a000ae1aefde
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34260789"
---
# <a name="azure-scheduler-modules-for-nodejs"></a><span data-ttu-id="06ce4-103">Módulos de Agendador do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="06ce4-103">Azure Scheduler modules for Node.js</span></span>

<span data-ttu-id="06ce4-104">O Agendador do Azure cria, mantém e invoca o trabalho agendado por meio de HTTP, HTTPS, uma fila de armazenamento ou do [Barramento de Serviço do Azure](/azure/service-bus-messaging/service-bus-messaging-overview).</span><span class="sxs-lookup"><span data-stu-id="06ce4-104">Azure Scheduler creates, maintains, and invokes scheduled work via HTTP, HTTPS, a storage queue, or the [Azure Service Bus](/azure/service-bus-messaging/service-bus-messaging-overview).</span></span>

<span data-ttu-id="06ce4-105">Saiba mais sobre o [Agendador do Azure](/azure/scheduler/scheduler-intro).</span><span class="sxs-lookup"><span data-stu-id="06ce4-105">Learn more about [Azure Scheduler](/azure/scheduler/scheduler-intro).</span></span>

## <a name="management-package"></a><span data-ttu-id="06ce4-106">Pacote de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="06ce4-106">Management package</span></span>

<span data-ttu-id="06ce4-107">Crie, mantenha e invoque o trabalho agendado em vários canais de comunicação com a API de gerenciamento.</span><span class="sxs-lookup"><span data-stu-id="06ce4-107">Create, maintain, and invoke scheduled work across various communication channels with the management API.</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="06ce4-108">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="06ce4-108">Install the npm module</span></span>

<span data-ttu-id="06ce4-109">Instalar o módulo npm de Agendador do Azure</span><span class="sxs-lookup"><span data-stu-id="06ce4-109">Install the Azure Scheduler npm module</span></span>

```bash
npm install azure-arm-scheduler
```

### <a name="example"></a><span data-ttu-id="06ce4-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="06ce4-110">Example</span></span>

<span data-ttu-id="06ce4-111">Este exemplo lista os agendadores atuais.</span><span class="sxs-lookup"><span data-stu-id="06ce4-111">This examples lists the current schedulers.</span></span>

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

## <a name="samples"></a><span data-ttu-id="06ce4-112">Exemplos</span><span class="sxs-lookup"><span data-stu-id="06ce4-112">Samples</span></span>

<span data-ttu-id="06ce4-113">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="06ce4-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
