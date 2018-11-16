---
title: Módulos de Backup do Azure para Node.js
description: Referência dos módulos do Backup do Azure para Node.js
author: markgalioto
ms.author: markgal
manager: carmonm
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Backup
ms.openlocfilehash: bf3e66ac8341cebd28dee20b6370ed3e5fbfbfa0
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51465762"
---
# <a name="azure-backup-modules-for-nodejs"></a>Módulos de Backup do Azure para Node.js

## <a name="overview"></a>Visão geral

O Backup do Azure é o serviço baseado no Azure que você pode usar para fazer backup (ou proteger) e restaurar os dados na nuvem da Microsoft. Ele substitui a solução de backup local ou externa existente por uma solução confiável, segura e econômica baseada em nuvem. O Backup do Azure oferece vários componentes que você pode baixar e implantar em um computador, servidor, ou na nuvem. O componente ou o agente que você implanta depende daquilo que deseja proteger. Todos os componentes do Backup do Azure (independentemente de você estar protegendo dados localmente ou na nuvem) podem ser usados para fazer backup de dados em um cofre dos Serviços de Recuperação no Azure. 

## <a name="management-package"></a>Pacote de gerenciamento

### <a name="install-the-modules-with-npm"></a>Instalar os módulos com npm

Use npm para instalar os módulos de Backup do Azure para Node.js

```bash
npm install azure-arm-recoveryservicesbackup
```

### <a name="example"></a>Exemplo

Este exemplo lista os trabalhos de recuperação para um determinado cofre e grupo de recursos.

```javascript
const msRestAzure = require('ms-rest-azure');
const RecoveryServicesBackupManagement = require('azure-arm-recoveryservicesbackup');

const subcriptionId = 'your-subscription-id';
const vault = 'your-recovery-service-vault';
const resourceGroupName = 'your-resource-group';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new RecoveryServicesBackupManagement(
      credentials,
      subcriptionId
    );
    return client.jobs.list(vault, resourceGroupName);
  })
  .then(jobs => console.dir(jobs, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a>Exemplos

Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.
