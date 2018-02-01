---
title: "Módulos de Aplicativos Lógicos do Azure para Node.js"
description: "Referência dos módulos de Aplicativos Lógicos do Azure para Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Logic Apps
ms.openlocfilehash: 37e485bea316ebd7fb4a064e1919da5501d96eac
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/26/2018
---
# <a name="azure-logic-apps-modules-for-nodejs"></a>Módulos de Aplicativos Lógicos do Azure para Node.js

Os Aplicativos Lógicos fornecem uma maneira de simplificar e implementar integrações escalonáveis e fluxos de trabalho na nuvem. Eles fornecem um designer visual para modelar e automatizar o processo como uma série de etapas conhecidas como fluxo de trabalho. Há muitos conectores locais e na nuvem para integrar rapidamente em serviços e protocolos. Um aplicativo lógico começa com um gatilho (como 'Quando uma conta é adicionada ao Dynamics CRM') e, após ser disparado, pode iniciar muitas ações de combinações, conversões e lógica de condição.

As vantagens de usar Aplicativos Lógicos incluem o seguinte:
- Menos tempo usado para criação de processos complexos devido ao uso de ferramentas de design fáceis de entender
- Implementação perfeita de padrões e fluxos de trabalho, que seriam difíceis de implementar no código
- Introdução rápida devido aos modelos
- Personalização do seu aplicativo lógico com seus próprios códigos, APIs e ações personalizados
- Conexão e sincronização com sistemas distintos locais e na nuvem
- Criado com base no BizTalk Server, Gerenciamento de API, Azure Functions e Barramento de Serviço do Azure com excelente suporte à integração

Os Aplicativos Lógicos são uma iPaaS (Plataforma de integração como um Serviço) totalmente gerenciada, que permite aos desenvolvedores não se preocuparem com hospedagem, escalabilidade, disponibilidade e gerenciamento. Os Aplicativos Lógicos serão escalados verticalmente de forma automática para atender à demanda.

## <a name="management-package"></a>Pacote de gerenciamento

### <a name="install-the-npm-module"></a>Instalar o módulo npm

Instalar o módulo de lógica do Azure para Node.js

```bash
npm install azure-arm-logic
```

### <a name="example"></a>Exemplo

```javascript
const msRestAzure = require('ms-rest-azure');
const LogicManagement = require('azure-arm-logic');

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const subscriptionId = 'subscription-id';
    const client = new LogicManagement(credentials, subscriptionId);
    return client.workflows.listBySubscription();
  })
  .then(workflows => console.log(workflows));
```

### <a name="samples"></a>Exemplos

Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.
