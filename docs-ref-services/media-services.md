---
title: Módulos de Serviços de Mídia do Azure para Node.js
description: Referência dos módulos de Serviços de Mídia do Azure para Node.js
author: Juliako
ms.author: juliako
manager: cfowler
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Media Services
ms.openlocfilehash: bfd4402c215a81c9ed8753cfe9ad9dbfaa52bd6f
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2018
ms.locfileid: "50269739"
---
# <a name="azure-media-services-modules-for-nodejs"></a>Módulos de Serviços de Mídia do Azure para Node.js

Os Serviços de Mídia do Azure são uma plataforma extensível baseada em nuvem que permite aos desenvolvedores compilar aplicativos de gerenciamento e entrega de mídia escalonável. Os serviços de mídia se baseiam em APIs REST que permitem que você carregue com segurança, armazene, codifique e empacote o conteúdo de áudio ou vídeo para entrega de streaming sob demanda e ao vivo para vários clientes (por exemplo, TV, PCs e dispositivos móveis).

Com os Serviços de Mídia do Azure, você pode:
- Compilar fluxos de trabalho de ponta a ponta usando completamente os Serviços de Mídia. 
- Use componentes de terceiros para algumas partes do seu fluxo de trabalho. Por exemplo, codifique usando um codificador de terceiros. Em seguida, carregue, proteja, empacote e entregue usando os serviços de mídia.
- Transmita seu conteúdo ao vivo ou forneça conteúdo sob demanda. O tópico também está vinculado a outros tópicos relevantes.

## <a name="management-package"></a>Pacote de Gerenciamento

### <a name="install-the-npm-module"></a>Instalar o módulo npm

Instalar o módulo npm de serviços de mídia do Azure

```bash
npm install azure-arm-mediaservices
```

### <a name="example"></a>Exemplo

Este exemplo lista todos os serviços de mídia para um grupo de recursos.

```javascript
const msRestAzure = require('ms-rest-azure');
const mediaServicesManagement = require('azure-arm-mediaservices');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
let mediaServicesClient;

msRestAzure.interactiveLogin().then(credentials => {
  mediaServicesClient = new mediaServicesManagement(credentials, subscriptionId);
  mediaServicesClient.mediaServiceOperations
    .listByResourceGroup(resourceGroup)
    .then(mediaServices => console.log('Retrieved media services: ', mediaServices));
});
```

## <a name="samples"></a>Exemplos

Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.
