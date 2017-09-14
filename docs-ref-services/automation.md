---
title: "Módulos de Automação do Azure para Node.js"
description: "Referência dos módulos da Automação do Azure para Node.js"
keywords: "Azure, SDK, API, Automação, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Automation
ms.openlocfilehash: 96861efce8eb95f567aa25f2304cb271d932d949
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-automation-modules-for-nodejs"></a>Módulos de Automação do Azure para Node.js

## <a name="overview"></a>Visão geral

A Automação do Azure fornece uma maneira para os usuários automatizarem tarefas manuais, longas, sujeitas a erros e repetidas com frequência que normalmente são executadas em um ambiente de nuvem e corporativo. A Automação economiza tempo e aumenta a confiabilidade das tarefas administrativas regulares e até mesmo agenda a sua execução automática em intervalos regulares. Você pode automatizar processos usando runbooks ou automatizar o gerenciamento de configuração usando Configuração de Estado Desejado.

## <a name="management-package"></a>Pacote de gerenciamento

### <a name="install-the-modules-with-npm"></a>Instalar os módulos com npm

Usar o npm para instalar os módulos da Automação do Azure para Node.js

```bash
npm install azure-arm-automation
```

### <a name="example"></a>Exemplo

Este exemplo lista as contas de automação.

```javascript
const msRestAzure = require('ms-rest-azure');
const AutomationManagement = require('azure-arm-automation');

const subcriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new AutomationManagement(credentials, subcriptionId);
    return client.automationAccounts.listByResourceGroup(resourceGroup);
  })
  .then(automationAccounts =>
    console.dir(automationAccounts, { depth: null, colors: true })
  )
  .catch(err => console.log(err));

```

## <a name="samples"></a>Exemplos

Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.
