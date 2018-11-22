---
title: Módulos de Assistente do Azure para Node.js
description: Referência dos módulos do Assistente do Azure para Node.js
author: KumudD
ms.author: kumud
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Advisor
ms.openlocfilehash: 54686220006d27341dbb50a249d0b2f44411b112
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2018
ms.locfileid: "52116541"
---
# <a name="azure-advisor-modules-for-nodejs"></a>Módulos de Assistente do Azure para Node.js

## <a name="overview"></a>Visão geral

O Azure Advisor é um consultor de nuvem personalizado que ajuda a seguir as práticas recomendadas para otimizar as implantações do Azure. O Assistente analisa a telemetria de uso e configuração do recurso e, depois, recomenda soluções que podem ajudar você a melhorar a economia, o desempenho, a alta disponibilidade e a segurança de seus recursos do Azure.

Com o Assistente, é possível:
- Obter recomendações de melhores práticas proativas, personalizadas e prontas para uso.
- Melhorar o desempenho, a segurança e a alta disponibilidade de seus recursos, enquanto você identifica oportunidades para reduzir o gasto geral do Azure.
- Obter recomendações com ações propostas embutidas.

## <a name="management-package"></a>Pacote de gerenciamento

### <a name="install-the-npm-module"></a>Instalar o módulo npm

Instalar o módulo npm do Assistente do Azure

```bash
npm install azure-arm-advisor
```

### <a name="example"></a>Exemplo

Este exemplo exibe a lista de recomendações do Assistente do Azure.

```javascript
const msRestAzure = require('ms-rest-azure');
const advisorManagement = require('azure-arm-advisor');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new advisorManagement(credentials, subscriptionId);
  client.recommendations.list().then(recommendations => {
    console.log('List of recommendations:');
    console.dir(recommendations, {depth: null, colors: true});
  });
});
```

## <a name="samples"></a>Exemplos

Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.
