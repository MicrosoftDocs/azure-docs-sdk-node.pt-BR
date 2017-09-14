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
# <a name="azure-scheduler-modules-for-nodejs"></a><span data-ttu-id="b75f1-104">Módulos de Agendador do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="b75f1-104">Azure Scheduler modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="b75f1-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="b75f1-105">Overview</span></span>

<span data-ttu-id="b75f1-106">O Agendador do Azure cria, mantém e invoca o trabalho agendado por meio de HTTP, HTTPS, uma fila de armazenamento ou do [Barramento de Serviço do Azure](/azure/service-bus-messaging/service-bus-messaging-overview).</span><span class="sxs-lookup"><span data-stu-id="b75f1-106">Azure Scheduler creates, maintains, and invokes scheduled work via HTTP, HTTPS, a storage queue, or the [Azure Service Bus](/azure/service-bus-messaging/service-bus-messaging-overview).</span></span>

<span data-ttu-id="b75f1-107">Saiba mais sobre o [Agendador do Azure](/azure/scheduler/scheduler-intro).</span><span class="sxs-lookup"><span data-stu-id="b75f1-107">Learn more about [Azure Scheduler](/azure/scheduler/scheduler-intro).</span></span>

## <a name="management-package"></a><span data-ttu-id="b75f1-108">Pacote de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="b75f1-108">Management package</span></span>

<span data-ttu-id="b75f1-109">Crie, mantenha e invoque o trabalho agendado em vários canais de comunicação com a API de gerenciamento.</span><span class="sxs-lookup"><span data-stu-id="b75f1-109">Create, maintain, and invoke scheduled work across various communication channels with the management API.</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="b75f1-110">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="b75f1-110">Install the npm module</span></span>

<span data-ttu-id="b75f1-111">Instalar o módulo npm de Agendador do Azure</span><span class="sxs-lookup"><span data-stu-id="b75f1-111">Install the Azure Scheduler npm module</span></span>

```bash
npm install azure-arm-scheduler
```

### <a name="example"></a><span data-ttu-id="b75f1-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b75f1-112">Example</span></span>

<span data-ttu-id="b75f1-113">Este exemplo lista os agendadores atuais.</span><span class="sxs-lookup"><span data-stu-id="b75f1-113">This examples lists the current schedulers.</span></span>

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

## <a name="samples"></a><span data-ttu-id="b75f1-114">Exemplos</span><span class="sxs-lookup"><span data-stu-id="b75f1-114">Samples</span></span>

<span data-ttu-id="b75f1-115">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="b75f1-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
