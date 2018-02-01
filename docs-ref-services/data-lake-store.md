---
title: "Módulos do Azure Data Lake Store do Node.js"
description: "Referência dos módulos do Azure Data Lake Store para Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Data Lake Store
ms.openlocfilehash: a108cc6d184b72d2d4227f9e60da6b7a535f92ae
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/26/2018
---
# <a name="azure-data-lake-store-modules-for-nodejs"></a><span data-ttu-id="a4334-103">Módulos do Azure Data Lake Store do Node.js</span><span class="sxs-lookup"><span data-stu-id="a4334-103">Azure Data Lake Store modules for Node.js</span></span>

<span data-ttu-id="a4334-104">O Repositório Azure Data Lake é um repositório em hiper-escala corporativo para cargas de trabalho de análise de big data.</span><span class="sxs-lookup"><span data-stu-id="a4334-104">Azure Data Lake Store is an enterprise-wide hyper-scale repository for big data analytic workloads.</span></span> <span data-ttu-id="a4334-105">O Azure Data Lake permite que você capture dados de qualquer tamanho, tipo e velocidade de ingestão em um único lugar para análises operacionais e exploratórias.</span><span class="sxs-lookup"><span data-stu-id="a4334-105">Azure Data Lake enables you to capture data of any size, type, and ingestion speed in one single place for operational and exploratory analytics.</span></span>

## <a name="management-package"></a><span data-ttu-id="a4334-106">Pacote de Gerenciamento</span><span class="sxs-lookup"><span data-stu-id="a4334-106">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="a4334-107">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="a4334-107">Install the npm module</span></span>

<span data-ttu-id="a4334-108">Usar npm para instalar os módulos do Azure Data Lake Store para Node.js</span><span class="sxs-lookup"><span data-stu-id="a4334-108">Use npm to install the Azure Data Lake Store modules for Node.js</span></span>

```bash
npm install azure-arm-datalake-store
```

### <a name="example"></a><span data-ttu-id="a4334-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a4334-109">Example</span></span>

<span data-ttu-id="a4334-110">Este exemplo lista todas as contas do Data Lake Store em determinada assinatura do Azure</span><span class="sxs-lookup"><span data-stu-id="a4334-110">This example lists all Data Lake Store accounts within a given Azure subscription</span></span>

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

## <a name="samples"></a><span data-ttu-id="a4334-111">Exemplos</span><span class="sxs-lookup"><span data-stu-id="a4334-111">Samples</span></span>

<span data-ttu-id="a4334-112">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="a4334-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
