---
title: Módulos de Assistente do Azure para Node.js
description: Referência dos módulos do Assistente do Azure para Node.js
author: KumudD
ms.author: kumud
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Advisor
ms.openlocfilehash: 54686220006d27341dbb50a249d0b2f44411b112
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2018
ms.locfileid: "50310923"
---
# <a name="azure-advisor-modules-for-nodejs"></a><span data-ttu-id="be793-103">Módulos de Assistente do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="be793-103">Azure Advisor modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="be793-104">Visão geral</span><span class="sxs-lookup"><span data-stu-id="be793-104">Overview</span></span>

<span data-ttu-id="be793-105">O Azure Advisor é um consultor de nuvem personalizado que ajuda a seguir as práticas recomendadas para otimizar as implantações do Azure.</span><span class="sxs-lookup"><span data-stu-id="be793-105">Azure Advisor is a personalized cloud consultant that helps you follow best practices to optimize your Azure deployments.</span></span> <span data-ttu-id="be793-106">O Assistente analisa a telemetria de uso e configuração do recurso e, depois, recomenda soluções que podem ajudar você a melhorar a economia, o desempenho, a alta disponibilidade e a segurança de seus recursos do Azure.</span><span class="sxs-lookup"><span data-stu-id="be793-106">Advisor analyzes your resource configuration and usage telemetry and then recommends solutions that can help you improve the cost effectiveness, performance, high availability, and security of your Azure resources.</span></span>

<span data-ttu-id="be793-107">Com o Assistente, é possível:</span><span class="sxs-lookup"><span data-stu-id="be793-107">With Advisor, you can:</span></span>
- <span data-ttu-id="be793-108">Obter recomendações de melhores práticas proativas, personalizadas e prontas para uso.</span><span class="sxs-lookup"><span data-stu-id="be793-108">Get proactive, actionable, and personalized best practices recommendations.</span></span>
- <span data-ttu-id="be793-109">Melhorar o desempenho, a segurança e a alta disponibilidade de seus recursos, enquanto você identifica oportunidades para reduzir o gasto geral do Azure.</span><span class="sxs-lookup"><span data-stu-id="be793-109">Improve the performance, security, and high availability of your resources, as you identify opportunities to reduce your overall Azure spend.</span></span>
- <span data-ttu-id="be793-110">Obter recomendações com ações propostas embutidas.</span><span class="sxs-lookup"><span data-stu-id="be793-110">Get recommendations with proposed actions inline.</span></span>

## <a name="management-package"></a><span data-ttu-id="be793-111">Pacote de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="be793-111">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="be793-112">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="be793-112">Install the npm module</span></span>

<span data-ttu-id="be793-113">Instalar o módulo npm do Assistente do Azure</span><span class="sxs-lookup"><span data-stu-id="be793-113">Install the Azure Advisor npm module</span></span>

```bash
npm install azure-arm-advisor
```

### <a name="example"></a><span data-ttu-id="be793-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="be793-114">Example</span></span>

<span data-ttu-id="be793-115">Este exemplo exibe a lista de recomendações do Assistente do Azure.</span><span class="sxs-lookup"><span data-stu-id="be793-115">This example displays the list of recommendations from Azure Advisor.</span></span>

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

## <a name="samples"></a><span data-ttu-id="be793-116">Exemplos</span><span class="sxs-lookup"><span data-stu-id="be793-116">Samples</span></span>

<span data-ttu-id="be793-117">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="be793-117">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
