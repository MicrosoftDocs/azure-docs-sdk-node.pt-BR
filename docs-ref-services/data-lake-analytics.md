---
title: "Módulos do Azure Data Lake Analytics para Node.js"
description: "Referência dos módulos do Azure Data Lake Analytics para Node.js"
keywords: Azure, SDK, API, Data Lake Analytics, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Data Lake Analytics
ms.openlocfilehash: 46f414ac6909de5bd956666baf51be1ca9d25ac7
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-data-lake-analytics-modules-for-nodejs"></a>Módulos do Azure Data Lake Analytics para Node.js

## <a name="overview"></a>Visão geral
O Azure Data Lake Analytics é um serviço de análise sob demanda que simplifica a análise de big data. Você pode se concentrar em escrever, executar e gerenciar trabalhos em vez de operar a infraestrutura distribuída. Em vez de implantar, configurar e ajustar o hardware, você escreve consultas para transformar seus dados e extrair informações importantes. O serviço de análise pode manipular trabalhos de qualquer escala de maneira instantânea, simplesmente configurando o controle para a quantidade de potência necessária. Você só paga pelo trabalho quando ele está em execução, o que o torna econômico. O serviço de análise dá suporte ao Active Directory do Azure, permitindo que você gerencie o acesso e as funções de maneira integrada com seu sistema de identidade local. Ele também inclui a U-SQL, uma linguagem que unifica os benefícios do SQL com a capacidade expressiva dos códigos do usuário. O tempo de execução distribuído escalonável do U-SQL permite que você analise de forma eficiente dados no repositório e em SQL Servers no Azure, no Banco de Dados SQL do Azure e no SQL Data Warehouse do Azure.

### <a name="management-package"></a>Pacote de gerenciamento

### <a name="install-the-npm-module"></a>Instalar o módulo npm

Usar npm para instalar os módulos do Azure Data Lake Analytics para Node.js

```bash
npm install azure-arm-datalake-analytics
```

### <a name="example"></a>Exemplo

Este exemplo lista todas as contas de análise para uma determinada assinatura.

```javascript
const msRestAzure = require('ms-rest-azure');
const adlsManagement = require('azure-arm-datalake-analytics');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const accountClient = new adlsManagement.DataLakeAnalyticsAccountClient(
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
