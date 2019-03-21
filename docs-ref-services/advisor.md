---
title: Módulos de Assistente do Azure para Node.js
description: Referência dos módulos do Assistente do Azure para Node.js
author: KumudD
ms.author: kumud
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.devlang: nodejs
ms.service: Advisor
ms.openlocfilehash: 952ac4bb67f4c177a06ce0ae3eb0fac7fa8ded54
ms.sourcegitcommit: 34172ad11850839ddd81d02841807e07f3761425
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58052581"
---
# <a name="azure-advisor-modules-for-nodejs"></a><span data-ttu-id="4d98e-103">Módulos de Assistente do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="4d98e-103">Azure Advisor modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="4d98e-104">Visão geral</span><span class="sxs-lookup"><span data-stu-id="4d98e-104">Overview</span></span>

<span data-ttu-id="4d98e-105">O Azure Advisor é um consultor de nuvem personalizado que ajuda a seguir as práticas recomendadas para otimizar as implantações do Azure.</span><span class="sxs-lookup"><span data-stu-id="4d98e-105">Azure Advisor is a personalized cloud consultant that helps you follow best practices to optimize your Azure deployments.</span></span> <span data-ttu-id="4d98e-106">O Assistente analisa a telemetria de uso e configuração do recurso e, depois, recomenda soluções que podem ajudar você a melhorar a economia, o desempenho, a alta disponibilidade e a segurança de seus recursos do Azure.</span><span class="sxs-lookup"><span data-stu-id="4d98e-106">Advisor analyzes your resource configuration and usage telemetry and then recommends solutions that can help you improve the cost effectiveness, performance, high availability, and security of your Azure resources.</span></span>

<span data-ttu-id="4d98e-107">Com o Assistente, é possível:</span><span class="sxs-lookup"><span data-stu-id="4d98e-107">With Advisor, you can:</span></span>
- <span data-ttu-id="4d98e-108">Obter recomendações de melhores práticas proativas, personalizadas e prontas para uso.</span><span class="sxs-lookup"><span data-stu-id="4d98e-108">Get proactive, actionable, and personalized best practices recommendations.</span></span>
- <span data-ttu-id="4d98e-109">Melhorar o desempenho, a segurança e a alta disponibilidade de seus recursos, enquanto você identifica oportunidades para reduzir o gasto geral do Azure.</span><span class="sxs-lookup"><span data-stu-id="4d98e-109">Improve the performance, security, and high availability of your resources, as you identify opportunities to reduce your overall Azure spend.</span></span>
- <span data-ttu-id="4d98e-110">Obter recomendações com ações propostas embutidas.</span><span class="sxs-lookup"><span data-stu-id="4d98e-110">Get recommendations with proposed actions inline.</span></span>

## <a name="management-package"></a><span data-ttu-id="4d98e-111">Pacote de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="4d98e-111">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="4d98e-112">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="4d98e-112">Install the npm module</span></span>

<span data-ttu-id="4d98e-113">Instalar o módulo npm do Assistente do Azure</span><span class="sxs-lookup"><span data-stu-id="4d98e-113">Install the Azure Advisor npm module</span></span>

```bash
npm install azure-arm-advisor
```

### <a name="example"></a><span data-ttu-id="4d98e-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4d98e-114">Example</span></span>

<span data-ttu-id="4d98e-115">Este exemplo exibe a lista de recomendações do Assistente do Azure.</span><span class="sxs-lookup"><span data-stu-id="4d98e-115">This example displays the list of recommendations from Azure Advisor.</span></span>

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

## <a name="samples"></a><span data-ttu-id="4d98e-116">Exemplos</span><span class="sxs-lookup"><span data-stu-id="4d98e-116">Samples</span></span>

<span data-ttu-id="4d98e-117">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="4d98e-117">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
