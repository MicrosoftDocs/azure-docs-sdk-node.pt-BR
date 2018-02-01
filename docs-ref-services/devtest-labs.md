---
title: "Módulos do Azure DevTest Labs para Node.js"
description: "Referência dos módulos do Azure DevTest Labs para Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: DevTest Labs
ms.openlocfilehash: 7754280741c09d47e138518d33628c667944c651
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/26/2018
---
# <a name="azure-devtest-labs-modules-for-nodejs"></a><span data-ttu-id="d48f2-103">Módulos do Azure DevTest Labs para Node.js</span><span class="sxs-lookup"><span data-stu-id="d48f2-103">Azure DevTest Labs modules for Node.js</span></span>

<span data-ttu-id="d48f2-104">Os Laboratórios de Desenvolvimento/Teste do Azure são um serviço que ajuda os desenvolvedores e testadores a rapidamente criar ambientes no Azure, minimizando o desperdício e o controle de custos.</span><span class="sxs-lookup"><span data-stu-id="d48f2-104">Azure DevTest Labs is a service that helps developers and testers quickly create environments in Azure while minimizing waste and controlling cost.</span></span> <span data-ttu-id="d48f2-105">Você pode testar a versão mais recente do seu aplicativo, provisionamento ambientes Windows e Linux rapidamente usando modelos reutilizáveis e artefatos.</span><span class="sxs-lookup"><span data-stu-id="d48f2-105">You can test the latest version of your application by quickly provisioning Windows and Linux environments using reusable templates and artifacts.</span></span> <span data-ttu-id="d48f2-106">Integre facilmente seu pipeline de implantação dos Laboratórios de Teste/Desenvolvimento para provisionar ambientes sob demanda.</span><span class="sxs-lookup"><span data-stu-id="d48f2-106">Easily integrate your deployment pipeline with DevTest Labs to provision on-demand environments.</span></span> <span data-ttu-id="d48f2-107">Dimensione seu teste de carga provisionando vários agentes de teste e crie ambientes previamente provisionados para treinamento e demonstrações.</span><span class="sxs-lookup"><span data-stu-id="d48f2-107">Scale up your load testing by provisioning multiple test agents, and create pre-provisioned environments for training and demos.</span></span>

## <a name="management-package"></a><span data-ttu-id="d48f2-108">Pacote de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="d48f2-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="d48f2-109">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="d48f2-109">Install the npm module</span></span>

<span data-ttu-id="d48f2-110">Instalar o módulo npm do Azure DevTest Labs</span><span class="sxs-lookup"><span data-stu-id="d48f2-110">Install the Azure DevTest Labs npm module</span></span>

```bash
npm install azure-arm-devtestlabs
```

### <a name="example"></a><span data-ttu-id="d48f2-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d48f2-111">Example</span></span>

<span data-ttu-id="d48f2-112">Este exemplo obtém e imprime os detalhes de um laboratório.</span><span class="sxs-lookup"><span data-stu-id="d48f2-112">This example gets and prints the details of a lab.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const DevTestLabsClient = require('azure-arm-devtestlabs');

const subscriptionId = 'your-subscription-id';
const resourceGroupName = 'your-resource-group-name';
const labName = 'your-lab-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new DevTestLabsClient(credentials, subscriptionId);
    return client.labOperations.getResource(resourceGroupName, labName);
  })
  .then(lab => {
    console.log('Details of lab:');
    console.dir(lab, { depth: null, colors: true });
  });


```

## <a name="samples"></a><span data-ttu-id="d48f2-113">Exemplos</span><span class="sxs-lookup"><span data-stu-id="d48f2-113">Samples</span></span>

<span data-ttu-id="d48f2-114">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="d48f2-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
