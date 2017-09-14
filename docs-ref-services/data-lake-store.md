---
title: "Módulos do Azure Data Lake Store do Node.js"
description: "Referência dos módulos do Azure Data Lake Store para Node.js"
keywords: Azure, SDK, API, Data Lake Store, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Data Lake Store
ms.openlocfilehash: 5885bf8f073e4f4f1ac2be88b8691b092e8a21d3
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-data-lake-store-modules-for-nodejs"></a>Módulos do Azure Data Lake Store do Node.js

## <a name="overview"></a>Visão geral
O Repositório Azure Data Lake é um repositório em hiper-escala corporativo para cargas de trabalho de análise de big data. O Azure Data Lake permite que você capture dados de qualquer tamanho, tipo e velocidade de ingestão em um único lugar para análises operacionais e exploratórias.

## <a name="management-package"></a>Pacote de Gerenciamento

### <a name="install-the-npm-module"></a>Instalar o módulo npm

Usar npm para instalar os módulos do Azure Data Lake Store para Node.js

```bash
npm install azure-arm-datalake-store
```

### <a name="example"></a>Exemplo

Este exemplo lista todas as contas do Data Lake Store em determinada assinatura do Azure

```javascript
const msRestAzure = require('ms-rest-azure');
const adlsManagement = require('azure-arm-datalake-store');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const accountClient = new adlsManagement.DataLakeStoreAccountClient(
    credentials,
    subscriptionId
  );
  accountClient.account.list().then(result => {
    console.log(result);
  });
});
```

## <a name="samples"></a>Exemplos

Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.
