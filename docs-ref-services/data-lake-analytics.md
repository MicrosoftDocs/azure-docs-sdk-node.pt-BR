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
# <a name="azure-data-lake-analytics-modules-for-nodejs"></a><span data-ttu-id="ff005-104">Módulos do Azure Data Lake Analytics para Node.js</span><span class="sxs-lookup"><span data-stu-id="ff005-104">Azure Data Lake Analytics modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="ff005-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="ff005-105">Overview</span></span>
<span data-ttu-id="ff005-106">O Azure Data Lake Analytics é um serviço de análise sob demanda que simplifica a análise de big data.</span><span class="sxs-lookup"><span data-stu-id="ff005-106">Azure Data Lake Analytics is an on-demand analytics job service to simplify big data analytics.</span></span> <span data-ttu-id="ff005-107">Você pode se concentrar em escrever, executar e gerenciar trabalhos em vez de operar a infraestrutura distribuída.</span><span class="sxs-lookup"><span data-stu-id="ff005-107">You can focus on writing, running, and managing jobs rather than on operating distributed infrastructure.</span></span> <span data-ttu-id="ff005-108">Em vez de implantar, configurar e ajustar o hardware, você escreve consultas para transformar seus dados e extrair informações importantes.</span><span class="sxs-lookup"><span data-stu-id="ff005-108">Instead of deploying, configuring, and tuning hardware, you write queries to transform your data and extract valuable insights.</span></span> <span data-ttu-id="ff005-109">O serviço de análise pode manipular trabalhos de qualquer escala de maneira instantânea, simplesmente configurando o controle para a quantidade de potência necessária.</span><span class="sxs-lookup"><span data-stu-id="ff005-109">The analytics service can handle jobs of any scale instantly by setting the dial for how much power you need.</span></span> <span data-ttu-id="ff005-110">Você só paga pelo trabalho quando ele está em execução, o que o torna econômico.</span><span class="sxs-lookup"><span data-stu-id="ff005-110">You only pay for your job when it is running, making it cost-effective.</span></span> <span data-ttu-id="ff005-111">O serviço de análise dá suporte ao Active Directory do Azure, permitindo que você gerencie o acesso e as funções de maneira integrada com seu sistema de identidade local.</span><span class="sxs-lookup"><span data-stu-id="ff005-111">The analytics service supports Azure Active Directory letting you manage access and roles, integrated with your on-premises identity system.</span></span> <span data-ttu-id="ff005-112">Ele também inclui a U-SQL, uma linguagem que unifica os benefícios do SQL com a capacidade expressiva dos códigos do usuário.</span><span class="sxs-lookup"><span data-stu-id="ff005-112">It also includes U-SQL, a language that unifies the benefits of SQL with the expressive power of user code.</span></span> <span data-ttu-id="ff005-113">O tempo de execução distribuído escalonável do U-SQL permite que você analise de forma eficiente dados no repositório e em SQL Servers no Azure, no Banco de Dados SQL do Azure e no SQL Data Warehouse do Azure.</span><span class="sxs-lookup"><span data-stu-id="ff005-113">U-SQL’s scalable distributed runtime enables you to efficiently analyze data in the store and across SQL Servers in Azure, Azure SQL Database, and Azure SQL Data Warehouse.</span></span>

### <a name="management-package"></a><span data-ttu-id="ff005-114">Pacote de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="ff005-114">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="ff005-115">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="ff005-115">Install the npm module</span></span>

<span data-ttu-id="ff005-116">Usar npm para instalar os módulos do Azure Data Lake Analytics para Node.js</span><span class="sxs-lookup"><span data-stu-id="ff005-116">Use npm to install the Azure Data Lake Analytics modules for Node.js</span></span>

```bash
npm install azure-arm-datalake-analytics
```

### <a name="example"></a><span data-ttu-id="ff005-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ff005-117">Example</span></span>

<span data-ttu-id="ff005-118">Este exemplo lista todas as contas de análise para uma determinada assinatura.</span><span class="sxs-lookup"><span data-stu-id="ff005-118">This example lists all of the analytics accounts for a given subscription.</span></span>

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

## <a name="samples"></a><span data-ttu-id="ff005-119">Exemplos</span><span class="sxs-lookup"><span data-stu-id="ff005-119">Samples</span></span>

<span data-ttu-id="ff005-120">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="ff005-120">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
