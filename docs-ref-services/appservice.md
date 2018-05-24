---
title: Módulos do Serviço de Aplicativo do Azure para Node.js
description: Referência dos módulos do Serviço de Aplicativo do Azure para Node.js
author: SyntaxC4
ms.author: cfowler
manager: jhubbard
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: appservice
ms.openlocfilehash: d9cb33e9aead2878fc9571b1ccb3a34b8990af74
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="azure-app-service-modules-for-nodejs"></a><span data-ttu-id="ae92c-103">Módulos do Serviço de Aplicativo do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="ae92c-103">Azure App Service modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="ae92c-104">Visão geral</span><span class="sxs-lookup"><span data-stu-id="ae92c-104">Overview</span></span>

<span data-ttu-id="ae92c-105">O Serviço de Aplicativo do Azure é uma oferta de PaaS (plataforma como serviço) do Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="ae92c-105">Azure App Service is a platform-as-a-service (PaaS) offering of Microsoft Azure.</span></span> <span data-ttu-id="ae92c-106">Crie aplicativos Web e móveis para qualquer plataforma ou dispositivo.</span><span class="sxs-lookup"><span data-stu-id="ae92c-106">Create web and mobile apps for any platform or device.</span></span> <span data-ttu-id="ae92c-107">Integre seus aplicativos a soluções SaaS, conecte-se com aplicativos locais e automatize os processos de negócios.</span><span class="sxs-lookup"><span data-stu-id="ae92c-107">Integrate your apps with SaaS solutions, connect with on-premises applications, and automate your business processes.</span></span> <span data-ttu-id="ae92c-108">O Azure executa os aplicativos em VMs (máquinas virtuais) totalmente gerenciadas, com sua escolha de recursos compartilhados de VM ou VMs dedicadas.</span><span class="sxs-lookup"><span data-stu-id="ae92c-108">Azure runs your apps on fully managed virtual machines (VMs), with your choice of shared VM resources or dedicated VMs.</span></span>

<span data-ttu-id="ae92c-109">O Serviço de Aplicativo inclui os recursos móveis e da Web que antes eram fornecidos separadamente, como os Sites do Azure e os Serviços Móveis do Azure.</span><span class="sxs-lookup"><span data-stu-id="ae92c-109">App Service includes the web and mobile capabilities that we previously delivered separately as Azure Websites and Azure Mobile Services.</span></span> <span data-ttu-id="ae92c-110">Ele também inclui novos recursos para automatizar processos empresariais e hospedagem de APIs de nuvem.</span><span class="sxs-lookup"><span data-stu-id="ae92c-110">It also includes new capabilities for automating business processes and hosting cloud APIs.</span></span> <span data-ttu-id="ae92c-111">Como um único serviço integrado, o Serviço de Aplicativo permite incluir vários componentes (sites, back-ends de aplicativo móvel, APIs RESTful e processos de negócios) em uma única solução.</span><span class="sxs-lookup"><span data-stu-id="ae92c-111">As a single integrated service, App Service lets you compose various components -- websites, mobile app back ends, RESTful APIs, and business processes -- into a single solution.</span></span>

## <a name="management-package"></a><span data-ttu-id="ae92c-112">Pacote de Gerenciamento</span><span class="sxs-lookup"><span data-stu-id="ae92c-112">Management Package</span></span>

### <a name="install-the-npm-package"></a><span data-ttu-id="ae92c-113">instalar o pacote npm</span><span class="sxs-lookup"><span data-stu-id="ae92c-113">Install the npm package</span></span>

<span data-ttu-id="ae92c-114">Instalar o módulo de Serviço de Aplicativo do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="ae92c-114">Install the Azure App Service module for Node.js</span></span>

```bash
npm install azure-arm-website
```

### <a name="example"></a><span data-ttu-id="ae92c-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ae92c-115">Example</span></span>

<span data-ttu-id="ae92c-116">Este exemplo cria um site no Azure usando o Node.js.</span><span class="sxs-lookup"><span data-stu-id="ae92c-116">This example creates a website on Azure using Node.js.</span></span>

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

## <a name="samples"></a><span data-ttu-id="ae92c-117">Exemplos</span><span class="sxs-lookup"><span data-stu-id="ae92c-117">Samples</span></span>

[!INCLUDE [node-appservice-samples](../docs-ref-conceptual/includes/appservice-samples.md)]

<span data-ttu-id="ae92c-118">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="ae92c-118">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
