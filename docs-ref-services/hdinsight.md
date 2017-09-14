---
title: "Módulos do Azure HDInsight para Node.js"
description: "Referência dos módulos do Azure HDInsight para Node.js"
keywords: Azure, SDK, API, HDInsight, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: HDInsight
ms.openlocfilehash: 1df988e98def42dcf33e90b4c3debece8cbe85e3
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-hdinsight-modules-for-nodejs"></a><span data-ttu-id="5744a-104">Módulos do Azure HDInsight para Node.js</span><span class="sxs-lookup"><span data-stu-id="5744a-104">Azure HDInsight Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="5744a-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="5744a-105">Overview</span></span>

<span data-ttu-id="5744a-106">O Azure HDInsight é uma distribuição em nuvem dos componentes do Hadoop da HDP (Hortonworks Data Platform).</span><span class="sxs-lookup"><span data-stu-id="5744a-106">Azure HDInsight is a cloud distribution of the Hadoop components from the Hortonworks Data Platform (HDP).</span></span> <span data-ttu-id="5744a-107">O Apache Hadoop era a estrutura de código-fonte original para processamento distribuído e análise de grandes conjuntos de dados em clusters de computadores.</span><span class="sxs-lookup"><span data-stu-id="5744a-107">Apache Hadoop was the original open-source framework for distributed processing and analysis of big data sets on clusters of computers.</span></span>

<span data-ttu-id="5744a-108">O HDInsight facilita o uso de tecnologias Hadoop com:</span><span class="sxs-lookup"><span data-stu-id="5744a-108">HDInsight makes Hadoop technologies easier to use, with:</span></span>
- <span data-ttu-id="5744a-109">Menos instalação e configuração.</span><span class="sxs-lookup"><span data-stu-id="5744a-109">Less setup and configuration.</span></span> <span data-ttu-id="5744a-110">Veja Provisionar clusters do Hadoop no HDInsight.</span><span class="sxs-lookup"><span data-stu-id="5744a-110">See Provision Hadoop clusters in HDInsight.</span></span>
- <span data-ttu-id="5744a-111">Alta disponibilidade e confiabilidade.</span><span class="sxs-lookup"><span data-stu-id="5744a-111">High availability and reliability.</span></span> <span data-ttu-id="5744a-112">Veja Disponibilidade e confiabilidade do HDInsight.</span><span class="sxs-lookup"><span data-stu-id="5744a-112">See HDInsight availability and reliability.</span></span>
- <span data-ttu-id="5744a-113">Segurança e governança por meio da integração com o Active Directory.</span><span class="sxs-lookup"><span data-stu-id="5744a-113">Security and governance through integration with Active Directory.</span></span> <span data-ttu-id="5744a-114">Veja Clusters ingressados no domínio.</span><span class="sxs-lookup"><span data-stu-id="5744a-114">See Domain-joined clusters.</span></span>
- <span data-ttu-id="5744a-115">Dimensionamento dinâmico sem interromper trabalhos</span><span class="sxs-lookup"><span data-stu-id="5744a-115">Dynamic scaling without interrupting jobs</span></span>
- <span data-ttu-id="5744a-116">Atualizações de componentes e versões atuais.</span><span class="sxs-lookup"><span data-stu-id="5744a-116">Component updates and current versions.</span></span> <span data-ttu-id="5744a-117">Veja Componentes do Hadoop e versões no HDInsight.</span><span class="sxs-lookup"><span data-stu-id="5744a-117">See Hadoop components and versions on HDInsight.</span></span>
- <span data-ttu-id="5744a-118">Integração com outros serviços do Azure, incluindo aplicativos Web e Banco de Dados SQL</span><span class="sxs-lookup"><span data-stu-id="5744a-118">Integration with other Azure services, including Web apps and SQL Database</span></span>

<span data-ttu-id="5744a-119">A pilha de tecnologias do Hadoop inclui software e utilitários relacionados, inclusive Apache Hive, HBase, Spark, Kafka e muitos outros.</span><span class="sxs-lookup"><span data-stu-id="5744a-119">The Hadoop technology stack includes related software and utilities, including Apache Hive, HBase, Spark, Kafka, and many others.</span></span> 

## <a name="management-package"></a><span data-ttu-id="5744a-120">Pacote de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="5744a-120">Management package</span></span>

### <a name="install-the-npm-modules"></a><span data-ttu-id="5744a-121">Instalar os módulos npm</span><span class="sxs-lookup"><span data-stu-id="5744a-121">Install the npm modules</span></span>

<span data-ttu-id="5744a-122">Usar npm para instalar os módulos do Azure HDInsight para Node.js</span><span class="sxs-lookup"><span data-stu-id="5744a-122">Use npm to install the Azure HDInsight modules for Node.js</span></span>

```bash
npm install azure-arm-hdinsight
```

```bash
azure-arm-hdinsight-jobs
```

### <a name="example"></a><span data-ttu-id="5744a-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5744a-123">Example</span></span> 

<span data-ttu-id="5744a-124">Este exemplo cria um cliente do HD Insight e então lista todos os grupos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="5744a-124">This example creates an HD Insight client and then lists all of the available clusters.</span></span> 

```javascript
const msRestAzure = require('ms-rest-azure');
const HDInsightManagementClient = require('azure-arm-hdinsight');

const subscriptionId = 'my-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
    const client = HDInsightManagementClient.createHDInsightManagementClient(
        credentials
    );

    credentials.subscriptionId = subscriptionId;

    client.clusters.list((err, result) => {
        console.log(result);
    });
});
```

## <a name="samples"></a><span data-ttu-id="5744a-125">Exemplos</span><span class="sxs-lookup"><span data-stu-id="5744a-125">Samples</span></span>

<span data-ttu-id="5744a-126">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="5744a-126">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
