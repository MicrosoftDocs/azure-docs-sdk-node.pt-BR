---
title: Módulos do Azure DevTest Labs para Node.js
description: Referência dos módulos do Azure DevTest Labs para Node.js
author: craigcaseyMSFT
ms.author: v-craic
manager: v-laurab
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: DevTest Labs
ms.openlocfilehash: 4528bf6a09bc86d23bfec982988added1aa3e257
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2018
ms.locfileid: "52133733"
---
# <a name="azure-devtest-labs-modules-for-nodejs"></a>Módulos do Azure DevTest Labs para Node.js

Os Laboratórios de Desenvolvimento/Teste do Azure são um serviço que ajuda os desenvolvedores e testadores a rapidamente criar ambientes no Azure, minimizando o desperdício e o controle de custos. Você pode testar a versão mais recente do seu aplicativo, provisionamento ambientes Windows e Linux rapidamente usando modelos reutilizáveis e artefatos. Integre facilmente seu pipeline de implantação dos Laboratórios de Teste/Desenvolvimento para provisionar ambientes sob demanda. Dimensione seu teste de carga provisionando vários agentes de teste e crie ambientes previamente provisionados para treinamento e demonstrações.

## <a name="management-package"></a>Pacote de gerenciamento

### <a name="install-the-npm-module"></a>Instalar o módulo npm

Instalar o módulo npm do Azure DevTest Labs

```bash
npm install azure-arm-devtestlabs
```

### <a name="example"></a>Exemplo

Este exemplo obtém e imprime os detalhes de um laboratório.

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

## <a name="samples"></a>Exemplos

Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.
