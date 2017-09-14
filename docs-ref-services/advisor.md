---
title: "Módulos de Assistente do Azure para Node.js"
description: "Referência dos módulos do Assistente do Azure para Node.js"
keywords: Azure, SDK, API, Assistente, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Advisor
ms.openlocfilehash: 9d0b22cd5f164cb0b1bb79a2cda1aceba0187ba5
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-advisor-modules-for-nodejs"></a><span data-ttu-id="34abc-104">Módulos de Assistente do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="34abc-104">Azure Advisor modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="34abc-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="34abc-105">Overview</span></span>

<span data-ttu-id="34abc-106">O Azure Advisor é um consultor de nuvem personalizado que ajuda a seguir as práticas recomendadas para otimizar as implantações do Azure.</span><span class="sxs-lookup"><span data-stu-id="34abc-106">Azure Advisor is a personalized cloud consultant that helps you follow best practices to optimize your Azure deployments.</span></span> <span data-ttu-id="34abc-107">O Assistente analisa a telemetria de uso e configuração do recurso e, depois, recomenda soluções que podem ajudar você a melhorar a economia, o desempenho, a alta disponibilidade e a segurança de seus recursos do Azure.</span><span class="sxs-lookup"><span data-stu-id="34abc-107">Advisor analyzes your resource configuration and usage telemetry and then recommends solutions that can help you improve the cost effectiveness, performance, high availability, and security of your Azure resources.</span></span>

<span data-ttu-id="34abc-108">Com o Assistente, é possível:</span><span class="sxs-lookup"><span data-stu-id="34abc-108">With Advisor, you can:</span></span>
- <span data-ttu-id="34abc-109">Obter recomendações de melhores práticas proativas, personalizadas e prontas para uso.</span><span class="sxs-lookup"><span data-stu-id="34abc-109">Get proactive, actionable, and personalized best practices recommendations.</span></span>
- <span data-ttu-id="34abc-110">Melhorar o desempenho, a segurança e a alta disponibilidade de seus recursos, enquanto você identifica oportunidades para reduzir o gasto geral do Azure.</span><span class="sxs-lookup"><span data-stu-id="34abc-110">Improve the performance, security, and high availability of your resources, as you identify opportunities to reduce your overall Azure spend.</span></span>
- <span data-ttu-id="34abc-111">Obter recomendações com ações propostas embutidas.</span><span class="sxs-lookup"><span data-stu-id="34abc-111">Get recommendations with proposed actions inline.</span></span>

## <a name="management-package"></a><span data-ttu-id="34abc-112">Pacote de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="34abc-112">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="34abc-113">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="34abc-113">Install the npm module</span></span>

<span data-ttu-id="34abc-114">Instalar o módulo npm do Assistente do Azure</span><span class="sxs-lookup"><span data-stu-id="34abc-114">Install the Azure Advisor npm module</span></span>

```bash
npm install azure-arm-advisor
```

### <a name="example"></a><span data-ttu-id="34abc-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34abc-115">Example</span></span>

<span data-ttu-id="34abc-116">Este exemplo exibe a lista de recomendações do Assistente do Azure.</span><span class="sxs-lookup"><span data-stu-id="34abc-116">This example displays the list of recommendations from Azure Advisor.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const advisorManagement = require('azure-arm-advisor');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new advisorManagement(credentials, subscriptionId);
  client.recommendations.list().then(recommendations => {
    console.log('List of recommendations:');
    console.dir(recommendations, {depth: null, colors: true});
  });
});
```

## <a name="samples"></a><span data-ttu-id="34abc-117">Exemplos</span><span class="sxs-lookup"><span data-stu-id="34abc-117">Samples</span></span>

<span data-ttu-id="34abc-118">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="34abc-118">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
