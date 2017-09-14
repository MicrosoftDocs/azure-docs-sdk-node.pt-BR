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
# <a name="azure-app-service-modules-for-nodejs"></a>Módulos do Serviço de Aplicativo do Azure para Node.js

## <a name="overview"></a>Visão geral

O Serviço de Aplicativo do Azure é uma oferta de PaaS (plataforma como serviço) do Microsoft Azure. Crie aplicativos Web e móveis para qualquer plataforma ou dispositivo. Integre seus aplicativos a soluções SaaS, conecte-se com aplicativos locais e automatize os processos de negócios. O Azure executa os aplicativos em VMs (máquinas virtuais) totalmente gerenciadas, com sua escolha de recursos compartilhados de VM ou VMs dedicadas.

O Serviço de Aplicativo inclui os recursos móveis e da Web que antes eram fornecidos separadamente, como os Sites do Azure e os Serviços Móveis do Azure. Ele também inclui novos recursos para automatizar processos empresariais e hospedagem de APIs de nuvem. Como um único serviço integrado, o Serviço de Aplicativo permite incluir vários componentes (sites, back-ends de aplicativo móvel, APIs RESTful e processos de negócios) em uma única solução.

## <a name="management-package"></a>Pacote de Gerenciamento

### <a name="install-the-npm-package"></a>instalar o pacote npm

Instalar o módulo de Serviço de Aplicativo do Azure para Node.js

```bash
npm install azure-arm-website
```

### <a name="example"></a>Exemplo

Este exemplo cria um site no Azure usando o Node.js.

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

## <a name="samples"></a>Exemplos

[!INCLUDE [node-appservice-samples](../docs-ref-conceptual/includes/appservice-samples.md)]

Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.
