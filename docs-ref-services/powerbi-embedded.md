---
title: Módulos do Power BI Embedded do Azure para Node.js
description: Referência dos módulos do Azure Power BI Embedded para Node.js
author: markingmyname
ms.author: maghan
manager: kfile
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: PowerBI Embedded
ms.openlocfilehash: 4d0a1ebf75591a9a3575172f325309ddbac7885c
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34260884"
---
# <a name="azure-powerbi-embedded-modules-for-nodejs"></a>Módulos do Power BI Embedded do Azure para Node.js

Com o serviço Power BI Embedded do Azure, você pode integrar relatórios do Power BI ao seu aplicativo de nó para criar ou editar gráficos e relatórios.

Saiba mais sobre o [Power BI Embedded](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding/).

## <a name="management-package"></a>Pacote de Gerenciamento

### <a name="install-the-npm-module"></a>Instalar o módulo npm

Instalar o módulo npm do Azure Power BI

```bash
npm install azure-arm-powerbiembedded
```

### <a name="example"></a>Exemplo

Este exemplo cria uma coleção de workspaces em um grupo de recursos existente.

```javascript
const msRestAzure = require('ms-rest-azure');
const PowerBIEmbeddedManagementClient = require('azure-arm-powerbiembedded');

const creationOptions = {
  location: 'northcentralus',
  tags: {
    key1: 'value1',
    key2: 'value2'
  },
  sku: {
    name: 'S1',
    teir: 'Standard'
  }
};

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group-name';
const workspace = 'workspace-collection-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new PowerBIEmbeddedManagementClient(
      credentials,
      subscriptionId
    );
    return client.workspaceCollections.create(
      resourceGroup,
      workspace,
      creationOptions
    );
  })
  .then(workspaces => console.dir(workspaces, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a>Exemplos

Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.
