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
# <a name="azure-data-lake-store-modules-for-nodejs"></a><span data-ttu-id="f6bed-104">Módulos do Azure Data Lake Store do Node.js</span><span class="sxs-lookup"><span data-stu-id="f6bed-104">Azure Data Lake Store modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="f6bed-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="f6bed-105">Overview</span></span>
<span data-ttu-id="f6bed-106">O Repositório Azure Data Lake é um repositório em hiper-escala corporativo para cargas de trabalho de análise de big data.</span><span class="sxs-lookup"><span data-stu-id="f6bed-106">Azure Data Lake Store is an enterprise-wide hyper-scale repository for big data analytic workloads.</span></span> <span data-ttu-id="f6bed-107">O Azure Data Lake permite que você capture dados de qualquer tamanho, tipo e velocidade de ingestão em um único lugar para análises operacionais e exploratórias.</span><span class="sxs-lookup"><span data-stu-id="f6bed-107">Azure Data Lake enables you to capture data of any size, type, and ingestion speed in one single place for operational and exploratory analytics.</span></span>

## <a name="management-package"></a><span data-ttu-id="f6bed-108">Pacote de Gerenciamento</span><span class="sxs-lookup"><span data-stu-id="f6bed-108">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="f6bed-109">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="f6bed-109">Install the npm module</span></span>

<span data-ttu-id="f6bed-110">Usar npm para instalar os módulos do Azure Data Lake Store para Node.js</span><span class="sxs-lookup"><span data-stu-id="f6bed-110">Use npm to install the Azure Data Lake Store modules for Node.js</span></span>

```bash
npm install azure-arm-datalake-store
```

### <a name="example"></a><span data-ttu-id="f6bed-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f6bed-111">Example</span></span>

<span data-ttu-id="f6bed-112">Este exemplo lista todas as contas do Data Lake Store em determinada assinatura do Azure</span><span class="sxs-lookup"><span data-stu-id="f6bed-112">This example lists all Data Lake Store accounts within a given Azure subscription</span></span>

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

## <a name="samples"></a><span data-ttu-id="f6bed-113">Exemplos</span><span class="sxs-lookup"><span data-stu-id="f6bed-113">Samples</span></span>

<span data-ttu-id="f6bed-114">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="f6bed-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
