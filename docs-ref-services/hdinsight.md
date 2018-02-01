---
title: "Módulos do Azure HDInsight para Node.js"
description: "Referência dos módulos do Azure HDInsight para Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: HDInsight
ms.openlocfilehash: 897ef2e3d2316a1f6f5637027ac2a2211c556f7a
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/26/2018
---
# <a name="azure-hdinsight-modules-for-nodejs"></a><span data-ttu-id="c8a0c-103">Módulos do Azure HDInsight para Node.js</span><span class="sxs-lookup"><span data-stu-id="c8a0c-103">Azure HDInsight Modules for Node.js</span></span>

<span data-ttu-id="c8a0c-104">O Azure HDInsight é uma distribuição em nuvem dos componentes do Hadoop da HDP (Hortonworks Data Platform).</span><span class="sxs-lookup"><span data-stu-id="c8a0c-104">Azure HDInsight is a cloud distribution of the Hadoop components from the Hortonworks Data Platform (HDP).</span></span> <span data-ttu-id="c8a0c-105">O Apache Hadoop era a estrutura de código-fonte original para processamento distribuído e análise de grandes conjuntos de dados em clusters de computadores.</span><span class="sxs-lookup"><span data-stu-id="c8a0c-105">Apache Hadoop was the original open-source framework for distributed processing and analysis of big data sets on clusters of computers.</span></span>

<span data-ttu-id="c8a0c-106">O HDInsight facilita o uso de tecnologias Hadoop com:</span><span class="sxs-lookup"><span data-stu-id="c8a0c-106">HDInsight makes Hadoop technologies easier to use, with:</span></span>
- <span data-ttu-id="c8a0c-107">Menos instalação e configuração.</span><span class="sxs-lookup"><span data-stu-id="c8a0c-107">Less setup and configuration.</span></span> <span data-ttu-id="c8a0c-108">Veja Provisionar clusters do Hadoop no HDInsight.</span><span class="sxs-lookup"><span data-stu-id="c8a0c-108">See Provision Hadoop clusters in HDInsight.</span></span>
- <span data-ttu-id="c8a0c-109">Alta disponibilidade e confiabilidade.</span><span class="sxs-lookup"><span data-stu-id="c8a0c-109">High availability and reliability.</span></span> <span data-ttu-id="c8a0c-110">Veja Disponibilidade e confiabilidade do HDInsight.</span><span class="sxs-lookup"><span data-stu-id="c8a0c-110">See HDInsight availability and reliability.</span></span>
- <span data-ttu-id="c8a0c-111">Segurança e governança por meio da integração com o Active Directory.</span><span class="sxs-lookup"><span data-stu-id="c8a0c-111">Security and governance through integration with Active Directory.</span></span> <span data-ttu-id="c8a0c-112">Veja Clusters ingressados no domínio.</span><span class="sxs-lookup"><span data-stu-id="c8a0c-112">See Domain-joined clusters.</span></span>
- <span data-ttu-id="c8a0c-113">Dimensionamento dinâmico sem interromper trabalhos</span><span class="sxs-lookup"><span data-stu-id="c8a0c-113">Dynamic scaling without interrupting jobs</span></span>
- <span data-ttu-id="c8a0c-114">Atualizações de componentes e versões atuais.</span><span class="sxs-lookup"><span data-stu-id="c8a0c-114">Component updates and current versions.</span></span> <span data-ttu-id="c8a0c-115">Veja Componentes do Hadoop e versões no HDInsight.</span><span class="sxs-lookup"><span data-stu-id="c8a0c-115">See Hadoop components and versions on HDInsight.</span></span>
- <span data-ttu-id="c8a0c-116">Integração com outros serviços do Azure, incluindo aplicativos Web e Banco de Dados SQL</span><span class="sxs-lookup"><span data-stu-id="c8a0c-116">Integration with other Azure services, including Web apps and SQL Database</span></span>

<span data-ttu-id="c8a0c-117">A pilha de tecnologias do Hadoop inclui software e utilitários relacionados, inclusive Apache Hive, HBase, Spark, Kafka e muitos outros.</span><span class="sxs-lookup"><span data-stu-id="c8a0c-117">The Hadoop technology stack includes related software and utilities, including Apache Hive, HBase, Spark, Kafka, and many others.</span></span> 

## <a name="management-package"></a><span data-ttu-id="c8a0c-118">Pacote de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="c8a0c-118">Management package</span></span>

### <a name="install-the-npm-modules"></a><span data-ttu-id="c8a0c-119">Instalar os módulos npm</span><span class="sxs-lookup"><span data-stu-id="c8a0c-119">Install the npm modules</span></span>

<span data-ttu-id="c8a0c-120">Usar npm para instalar os módulos do Azure HDInsight para Node.js</span><span class="sxs-lookup"><span data-stu-id="c8a0c-120">Use npm to install the Azure HDInsight modules for Node.js</span></span>

```bash
npm install azure-arm-hdinsight
```

```bash
azure-arm-hdinsight-jobs
```

### <a name="example"></a><span data-ttu-id="c8a0c-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c8a0c-121">Example</span></span> 

<span data-ttu-id="c8a0c-122">Este exemplo cria um cliente do HD Insight e então lista todos os grupos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="c8a0c-122">This example creates an HD Insight client and then lists all of the available clusters.</span></span> 

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

## <a name="samples"></a><span data-ttu-id="c8a0c-123">Exemplos</span><span class="sxs-lookup"><span data-stu-id="c8a0c-123">Samples</span></span>

<span data-ttu-id="c8a0c-124">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="c8a0c-124">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
