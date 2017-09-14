---
title: "Módulos de Aplicativos Lógicos do Azure para Node.js"
description: "Referência dos módulos de Aplicativos Lógicos do Azure para Node.js"
keywords: "Azure, SDK, API, Aplicativos Lógicos, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Logic Apps
ms.openlocfilehash: 70380dbf1fd199ba4909975b05ade72efaa4e0ec
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-logic-apps-modules-for-nodejs"></a><span data-ttu-id="bd552-104">Módulos de Aplicativos Lógicos do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="bd552-104">Azure Logic Apps modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="bd552-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="bd552-105">Overview</span></span>
<span data-ttu-id="bd552-106">Os Aplicativos Lógicos fornecem uma maneira de simplificar e implementar integrações escalonáveis e fluxos de trabalho na nuvem.</span><span class="sxs-lookup"><span data-stu-id="bd552-106">Logic Apps provide a way to simplify and implement scalable integrations and workflows in the cloud.</span></span> <span data-ttu-id="bd552-107">Eles fornecem um designer visual para modelar e automatizar o processo como uma série de etapas conhecidas como fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="bd552-107">It provides a visual designer to model and automate your process as a series of steps known as a workflow.</span></span> <span data-ttu-id="bd552-108">Há muitos conectores locais e na nuvem para integrar rapidamente em serviços e protocolos.</span><span class="sxs-lookup"><span data-stu-id="bd552-108">There are many connectors across the cloud and on-premises to quickly integrate across services and protocols.</span></span> <span data-ttu-id="bd552-109">Um aplicativo lógico começa com um gatilho (como 'Quando uma conta é adicionada ao Dynamics CRM') e, após ser disparado, pode iniciar muitas ações de combinações, conversões e lógica de condição.</span><span class="sxs-lookup"><span data-stu-id="bd552-109">A logic app begins with a trigger (like 'When an account is added to Dynamics CRM') and after firing can begin many combinations of actions, conversions, and condition logic.</span></span>

<span data-ttu-id="bd552-110">As vantagens de usar Aplicativos Lógicos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="bd552-110">The advantages of using Logic Apps include the following:</span></span>
- <span data-ttu-id="bd552-111">Menos tempo usado para criação de processos complexos devido ao uso de ferramentas de design fáceis de entender</span><span class="sxs-lookup"><span data-stu-id="bd552-111">Saving time by designing complex processes using easy to understand design tools</span></span>
- <span data-ttu-id="bd552-112">Implementação perfeita de padrões e fluxos de trabalho, que seriam difíceis de implementar no código</span><span class="sxs-lookup"><span data-stu-id="bd552-112">Implementing patterns and workflows seamlessly, that would otherwise be difficult to implement in code</span></span>
- <span data-ttu-id="bd552-113">Introdução rápida devido aos modelos</span><span class="sxs-lookup"><span data-stu-id="bd552-113">Getting started quickly from templates</span></span>
- <span data-ttu-id="bd552-114">Personalização do seu aplicativo lógico com seus próprios códigos, APIs e ações personalizados</span><span class="sxs-lookup"><span data-stu-id="bd552-114">Customizing your logic app with your own custom APIs, code, and actions</span></span>
- <span data-ttu-id="bd552-115">Conexão e sincronização com sistemas distintos locais e na nuvem</span><span class="sxs-lookup"><span data-stu-id="bd552-115">Connect and synchronise disparate systems across on-premises and the cloud</span></span>
- <span data-ttu-id="bd552-116">Criado com base no BizTalk Server, Gerenciamento de API, Azure Functions e Barramento de Serviço do Azure com excelente suporte à integração</span><span class="sxs-lookup"><span data-stu-id="bd552-116">Build off of BizTalk server, API Management, Azure Functions, and Azure Service Bus with first-class integration support</span></span>

<span data-ttu-id="bd552-117">Os Aplicativos Lógicos são uma iPaaS (Plataforma de integração como um Serviço) totalmente gerenciada, que permite aos desenvolvedores não se preocuparem com hospedagem, escalabilidade, disponibilidade e gerenciamento.</span><span class="sxs-lookup"><span data-stu-id="bd552-117">Logic Apps is a fully managed iPaaS (integration Platform as a Service) allowing developers not to have to worry about building hosting, scalability, availability and management.</span></span> <span data-ttu-id="bd552-118">Os Aplicativos Lógicos serão escalados verticalmente de forma automática para atender à demanda.</span><span class="sxs-lookup"><span data-stu-id="bd552-118">Logic Apps will scale up automatically to meet demand.</span></span>

## <a name="management-package"></a><span data-ttu-id="bd552-119">Pacote de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="bd552-119">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="bd552-120">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="bd552-120">Install the npm module</span></span>

<span data-ttu-id="bd552-121">Instalar o módulo de lógica do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="bd552-121">Install the Azure logic module for Node.js</span></span>

```bash
npm install azure-arm-logic
```

### <a name="example"></a><span data-ttu-id="bd552-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bd552-122">Example</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const LogicManagement = require('azure-arm-logic');

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const subscriptionId = 'subscription-id';
    const client = new LogicManagement(credentials, subscriptionId);
    return client.workflows.listBySubscription();
  })
  .then(workflows => console.log(workflows));
```

### <a name="samples"></a><span data-ttu-id="bd552-123">Exemplos</span><span class="sxs-lookup"><span data-stu-id="bd552-123">Samples</span></span>

<span data-ttu-id="bd552-124">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="bd552-124">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
