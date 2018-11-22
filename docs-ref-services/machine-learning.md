---
title: Módulos do Azure Machine Learning para Node.js
description: Referência dos módulos do Azure Machine Learning para Node.js
author: hning86
ms.author: haining
manager: mwinkle
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Machine Learning
ms.openlocfilehash: 7e39084c65a40e47ed61cc01daf994aff447690e
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2018
ms.locfileid: "52094372"
---
# <a name="azure-machine-learning-modules-for-nodejs"></a><span data-ttu-id="ac16b-103">Módulos do Azure Machine Learning para Node.js</span><span class="sxs-lookup"><span data-stu-id="ac16b-103">Azure Machine Learning modules for Node.js</span></span>

<span data-ttu-id="ac16b-104">O aprendizado de máquina é uma técnica da ciência de dados que ajuda os computadores a aprenderem com os dados existentes para preverem as tendências, resultados e futuros comportamentos.</span><span class="sxs-lookup"><span data-stu-id="ac16b-104">Machine learning is a technique of data science that helps computers learn from existing data in order to forecast future behaviors, outcomes, and trends.</span></span> <span data-ttu-id="ac16b-105">Essas estimativas ou previsões de aprendizado de máquina podem tornar aplicativos e dispositivos mais inteligentes.</span><span class="sxs-lookup"><span data-stu-id="ac16b-105">These forecasts or predictions from machine learning can make apps and devices smarter.</span></span> <span data-ttu-id="ac16b-106">Quando você faz compras online, o aprendizado de máquina ajuda a recomendar outros produtos que podem lhe agradar com base no que você já comprou.</span><span class="sxs-lookup"><span data-stu-id="ac16b-106">When you shop online, machine learning helps recommend other products you might like based on what you've purchased.</span></span> <span data-ttu-id="ac16b-107">Ao passar seu cartão de crédito, o aprendizado de máquina compara a transação com um banco de dados de transações e ajuda a detectar fraudes.</span><span class="sxs-lookup"><span data-stu-id="ac16b-107">When your credit card is swiped, machine learning compares the transaction to a database of transactions and helps detect fraud.</span></span> <span data-ttu-id="ac16b-108">Quando o aspirador de pó robô aspira uma sala, o aprendizado de máquina ajuda a decidir se o trabalho é feito ou não.</span><span class="sxs-lookup"><span data-stu-id="ac16b-108">When your robot vacuum cleaner vacuums a room, machine learning helps it decide whether the job is done.</span></span>

## <a name="management-package"></a><span data-ttu-id="ac16b-109">Pacote de Gerenciamento</span><span class="sxs-lookup"><span data-stu-id="ac16b-109">Management Package</span></span>


### <a name="install-the-npm-module"></a><span data-ttu-id="ac16b-110">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="ac16b-110">Install the npm module</span></span>

<span data-ttu-id="ac16b-111">Instalar o módulo npm do Azure Machine Learning</span><span class="sxs-lookup"><span data-stu-id="ac16b-111">Install the Azure Machine Learning npm module</span></span>

```bash
npm install azure-arm-machinelearning
```

### <a name="example"></a><span data-ttu-id="ac16b-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ac16b-112">Example</span></span>

<span data-ttu-id="ac16b-113">Este exemplo lista todos os planos do compromisso de machine learning.</span><span class="sxs-lookup"><span data-stu-id="ac16b-113">This example lists all machine learning committment plans.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const MachineLearningManagement = require('azure-arm-machinelearning');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new MachineLearningManagement.CommitmentPlansManagementClient(
      credentials,
      subscriptionId
    );
    return client.commitmentPlans.list();
  })
  .then(commitmentPlans => {
    console.log('List of commitmentPlans:');
    console.dir(commitmentPlans, { depth: null, colors: true });
  });
```

## <a name="samples"></a><span data-ttu-id="ac16b-114">Exemplos</span><span class="sxs-lookup"><span data-stu-id="ac16b-114">Samples</span></span>

<span data-ttu-id="ac16b-115">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="ac16b-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
