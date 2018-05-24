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
