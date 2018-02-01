---
title: "Módulos do Azure Machine Learning para Node.js"
description: "Referência dos módulos do Azure Machine Learning para Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Machine Learning
ms.openlocfilehash: 82f731971505250f1d637ae32b4c7a83ff24fccf
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/26/2018
---
# <a name="azure-machine-learning-modules-for-nodejs"></a>Módulos do Azure Machine Learning para Node.js

O aprendizado de máquina é uma técnica da ciência de dados que ajuda os computadores a aprenderem com os dados existentes para preverem as tendências, resultados e futuros comportamentos. Essas estimativas ou previsões de aprendizado de máquina podem tornar aplicativos e dispositivos mais inteligentes. Quando você faz compras online, o aprendizado de máquina ajuda a recomendar outros produtos que podem lhe agradar com base no que você já comprou. Ao passar seu cartão de crédito, o aprendizado de máquina compara a transação com um banco de dados de transações e ajuda a detectar fraudes. Quando o aspirador de pó robô aspira uma sala, o aprendizado de máquina ajuda a decidir se o trabalho é feito ou não.

## <a name="management-package"></a>Pacote de Gerenciamento


### <a name="install-the-npm-module"></a>Instalar o módulo npm

Instalar o módulo npm do Azure Machine Learning

```bash
npm install azure-arm-machinelearning
```

### <a name="example"></a>Exemplo

Este exemplo lista todos os planos do compromisso de machine learning.

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

## <a name="samples"></a>Exemplos

Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.
