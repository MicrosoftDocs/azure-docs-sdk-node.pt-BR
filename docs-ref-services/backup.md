---
title: Módulos de Backup do Azure para Node.js
description: Referência dos módulos do Backup do Azure para Node.js
author: markgalioto
ms.author: markgal
manager: carmonm
ms.date: 07/18/2017
ms.topic: article
ms.devlang: nodejs
ms.service: Backup
ms.openlocfilehash: 9234285d32bc465eeb86d13514783e1de4e5ef1b
ms.sourcegitcommit: 34172ad11850839ddd81d02841807e07f3761425
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58052783"
---
# <a name="azure-backup-modules-for-nodejs"></a><span data-ttu-id="94006-103">Módulos de Backup do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="94006-103">Azure Backup Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="94006-104">Visão geral</span><span class="sxs-lookup"><span data-stu-id="94006-104">Overview</span></span>

<span data-ttu-id="94006-105">O Backup do Azure é o serviço baseado no Azure que você pode usar para fazer backup (ou proteger) e restaurar os dados na nuvem da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="94006-105">Azure Backup is the Azure-based service you can use to back up (or protect) and restore your data in the Microsoft cloud.</span></span> <span data-ttu-id="94006-106">Ele substitui a solução de backup local ou externa existente por uma solução confiável, segura e econômica baseada em nuvem.</span><span class="sxs-lookup"><span data-stu-id="94006-106">Azure Backup replaces your existing on-premises or off-site backup solution with a cloud-based solution that is reliable, secure, and cost-competitive.</span></span> <span data-ttu-id="94006-107">O Backup do Azure oferece vários componentes que você pode baixar e implantar em um computador, servidor, ou na nuvem.</span><span class="sxs-lookup"><span data-stu-id="94006-107">Azure Backup offers multiple components that you download and deploy on the appropriate computer, server, or in the cloud.</span></span> <span data-ttu-id="94006-108">O componente ou o agente que você implanta depende daquilo que deseja proteger.</span><span class="sxs-lookup"><span data-stu-id="94006-108">The component, or agent, that you deploy depends on what you want to protect.</span></span> <span data-ttu-id="94006-109">Todos os componentes do Backup do Azure (independentemente de você estar protegendo dados localmente ou na nuvem) podem ser usados para fazer backup de dados em um cofre dos Serviços de Recuperação no Azure.</span><span class="sxs-lookup"><span data-stu-id="94006-109">All Azure Backup components (no matter whether you're protecting data on-premises or in the cloud) can be used to back up data to a Recovery Services vault in Azure.</span></span> 

## <a name="management-package"></a><span data-ttu-id="94006-110">Pacote de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="94006-110">Management package</span></span>

### <a name="install-the-modules-with-npm"></a><span data-ttu-id="94006-111">Instalar os módulos com npm</span><span class="sxs-lookup"><span data-stu-id="94006-111">Install the modules with npm</span></span>

<span data-ttu-id="94006-112">Use npm para instalar os módulos de Backup do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="94006-112">Use npm to install the Azure Backup modules for Node.js</span></span>

```bash
npm install azure-arm-recoveryservicesbackup
```

### <a name="example"></a><span data-ttu-id="94006-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="94006-113">Example</span></span>

<span data-ttu-id="94006-114">Este exemplo lista os trabalhos de recuperação para um determinado cofre e grupo de recursos.</span><span class="sxs-lookup"><span data-stu-id="94006-114">This example lists the recovery jobs for a given vault and resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="94006-115">Exemplos</span><span class="sxs-lookup"><span data-stu-id="94006-115">Samples</span></span>

<span data-ttu-id="94006-116">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="94006-116">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
