---
title: "Módulos do Serviço de Aplicativo do Azure para Node.js"
description: "Referência dos módulos do Serviço de Aplicativo do Azure para Node.js"
keywords: Azure, Node, SDK, API, aplicativos web, celular, nodejs, javascript
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: appservice
ms.openlocfilehash: c695ae6d523ea731b18382ba0906f78b40ce301f
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-app-service-modules-for-nodejs"></a><span data-ttu-id="2ad7b-104">Módulos do Serviço de Aplicativo do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="2ad7b-104">Azure App Service modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="2ad7b-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="2ad7b-105">Overview</span></span>

<span data-ttu-id="2ad7b-106">O Serviço de Aplicativo do Azure é uma oferta de PaaS (plataforma como serviço) do Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="2ad7b-106">Azure App Service is a platform-as-a-service (PaaS) offering of Microsoft Azure.</span></span> <span data-ttu-id="2ad7b-107">Crie aplicativos Web e móveis para qualquer plataforma ou dispositivo.</span><span class="sxs-lookup"><span data-stu-id="2ad7b-107">Create web and mobile apps for any platform or device.</span></span> <span data-ttu-id="2ad7b-108">Integre seus aplicativos a soluções SaaS, conecte-se com aplicativos locais e automatize os processos de negócios.</span><span class="sxs-lookup"><span data-stu-id="2ad7b-108">Integrate your apps with SaaS solutions, connect with on-premises applications, and automate your business processes.</span></span> <span data-ttu-id="2ad7b-109">O Azure executa os aplicativos em VMs (máquinas virtuais) totalmente gerenciadas, com sua escolha de recursos compartilhados de VM ou VMs dedicadas.</span><span class="sxs-lookup"><span data-stu-id="2ad7b-109">Azure runs your apps on fully managed virtual machines (VMs), with your choice of shared VM resources or dedicated VMs.</span></span>

<span data-ttu-id="2ad7b-110">O Serviço de Aplicativo inclui os recursos móveis e da Web que antes eram fornecidos separadamente, como os Sites do Azure e os Serviços Móveis do Azure.</span><span class="sxs-lookup"><span data-stu-id="2ad7b-110">App Service includes the web and mobile capabilities that we previously delivered separately as Azure Websites and Azure Mobile Services.</span></span> <span data-ttu-id="2ad7b-111">Ele também inclui novos recursos para automatizar processos empresariais e hospedagem de APIs de nuvem.</span><span class="sxs-lookup"><span data-stu-id="2ad7b-111">It also includes new capabilities for automating business processes and hosting cloud APIs.</span></span> <span data-ttu-id="2ad7b-112">Como um único serviço integrado, o Serviço de Aplicativo permite incluir vários componentes (sites, back-ends de aplicativo móvel, APIs RESTful e processos de negócios) em uma única solução.</span><span class="sxs-lookup"><span data-stu-id="2ad7b-112">As a single integrated service, App Service lets you compose various components -- websites, mobile app back ends, RESTful APIs, and business processes -- into a single solution.</span></span>

## <a name="management-package"></a><span data-ttu-id="2ad7b-113">Pacote de Gerenciamento</span><span class="sxs-lookup"><span data-stu-id="2ad7b-113">Management Package</span></span>

### <a name="install-the-npm-package"></a><span data-ttu-id="2ad7b-114">instalar o pacote npm</span><span class="sxs-lookup"><span data-stu-id="2ad7b-114">Install the npm package</span></span>

<span data-ttu-id="2ad7b-115">Instalar o módulo de Serviço de Aplicativo do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="2ad7b-115">Install the Azure App Service module for Node.js</span></span>

```bash
npm install azure-arm-website
```

### <a name="example"></a><span data-ttu-id="2ad7b-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2ad7b-116">Example</span></span>

<span data-ttu-id="2ad7b-117">Este exemplo cria um site no Azure usando o Node.js.</span><span class="sxs-lookup"><span data-stu-id="2ad7b-117">This example creates a website on Azure using Node.js.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const webSiteManagementClient = require('azure-arm-website');

const subscriptionId = 'your-subscription-id';
const website = 'website001';
const resourceGroup = 'your-resource-group';
const hostingPlan = 'testHostingPlan';
let webSiteClient;

msRestAzure.interactiveLogin().then(credentials => {
  webSiteClient = new webSiteManagementClient(credentials, subscriptionId);
  createWebSite(website).then(website => console.log('Web Site created successfully', website));
});

function createWebSite(webSiteName) {
  const parameters = { location: 'westus', serverFarmId: hostingPlan };
  console.log(`Creating web site:  ${webSiteName}`);
  return webSiteClient.webApps.createOrUpdate(resourceGroup, webSiteName, parameters, null);
}
```

## <a name="samples"></a><span data-ttu-id="2ad7b-118">Exemplos</span><span class="sxs-lookup"><span data-stu-id="2ad7b-118">Samples</span></span>

[!INCLUDE [node-appservice-samples](../docs-ref-conceptual/includes/appservice-samples.md)]

<span data-ttu-id="2ad7b-119">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="2ad7b-119">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
