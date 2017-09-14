---
title: "Módulos de Hubs de Notificação do Azure para Node.js"
description: "Referência dos módulos de Hubs de Notificação do Azure para Node.js"
keywords: "Azure, SDK, API, Hubs de Notificação, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Notification Hubs
ms.openlocfilehash: 0141760cb93c77faed4a04893fe1376e4e75c361
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-notification-hubs-modules-for-nodejs"></a><span data-ttu-id="c7c6d-104">Módulos de Hubs de Notificação do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="c7c6d-104">Azure Notification Hubs modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="c7c6d-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="c7c6d-105">Overview</span></span>

<span data-ttu-id="c7c6d-106">Os Hubs de Notificação do Azure fornecem um mecanismo de envio por push fácil de usar, multiplataforma e dimensionável.</span><span class="sxs-lookup"><span data-stu-id="c7c6d-106">Azure Notification Hubs provide an easy-to-use, multi-platform, scaled-out push engine.</span></span> <span data-ttu-id="c7c6d-107">Com uma chamada à API única entre plataformas, você pode enviar notificações por push direcionadas e personalizadas para qualquer plataforma móvel de qualquer back-end local ou em nuvem.</span><span class="sxs-lookup"><span data-stu-id="c7c6d-107">With a single cross-platform API call, you can easily send targeted and personalized push notifications to any mobile platform from any cloud or on-premises backend.</span></span>

<span data-ttu-id="c7c6d-108">Os Hubs de Notificação funcionam bem tanto para cenários empresariais quanto para cenários de consumidor.</span><span class="sxs-lookup"><span data-stu-id="c7c6d-108">Notification Hubs works great for both enterprise and consumer scenarios.</span></span> <span data-ttu-id="c7c6d-109">Aqui temos alguns exemplos de como os consumidores usam os Hubs de Notificação:</span><span class="sxs-lookup"><span data-stu-id="c7c6d-109">Here are a few examples customers use Notification Hubs for:</span></span>
- <span data-ttu-id="c7c6d-110">Para enviar notificações sobre as novidades para milhões de pessoas com baixa latência.</span><span class="sxs-lookup"><span data-stu-id="c7c6d-110">Send breaking news notifications to millions with low latency.</span></span>
- <span data-ttu-id="c7c6d-111">Para enviar cupons baseados na localização para segmentos de usuários interessados.</span><span class="sxs-lookup"><span data-stu-id="c7c6d-111">Send location-based coupons to interested user segments.</span></span>
- <span data-ttu-id="c7c6d-112">Para enviar notificações de eventos para usuários ou grupos em aplicativos de mídia/esportes/finanças/jogos.</span><span class="sxs-lookup"><span data-stu-id="c7c6d-112">Send event-related notifications to users or groups for media/sports/finance/gaming applications.</span></span>
- <span data-ttu-id="c7c6d-113">Para enviar por push conteúdos promocionais para aplicativos com o objetivo de atrair e vender para os clientes.</span><span class="sxs-lookup"><span data-stu-id="c7c6d-113">Push promotional contents to apps to engage and market to customers.</span></span>
- <span data-ttu-id="c7c6d-114">Para notificar os usuários sobre eventos corporativos, como novas mensagens e itens de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c7c6d-114">Notify users of enterprise events like new messages and work items.</span></span>
- <span data-ttu-id="c7c6d-115">Para enviar códigos para Autenticação Multifator.</span><span class="sxs-lookup"><span data-stu-id="c7c6d-115">Send codes for multi-factor authentication.</span></span>

## <a name="management-package"></a><span data-ttu-id="c7c6d-116">Pacote de Gerenciamento</span><span class="sxs-lookup"><span data-stu-id="c7c6d-116">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="c7c6d-117">Instalar o módulo npm</span><span class="sxs-lookup"><span data-stu-id="c7c6d-117">Install the npm module</span></span>

<span data-ttu-id="c7c6d-118">Instalar o módulo de Hubs de Notificação do Azure</span><span class="sxs-lookup"><span data-stu-id="c7c6d-118">Install the Azure Notification Hubs module</span></span> 

```bash
npm install azure-arm-notificationhubs
```

### <a name="example"></a><span data-ttu-id="c7c6d-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c7c6d-119">Example</span></span>

<span data-ttu-id="c7c6d-120">Este exemplo lista todos os hubs de notificação.</span><span class="sxs-lookup"><span data-stu-id="c7c6d-120">This example lists all notification hubs.</span></span>

 ```javascript
const msRestAzure = require('ms-rest-azure');
const notificationHubsManagementClient = require('azure-arm-notificationhubs');

const subscriptionId = 'your-subscription-id';
const notificationHubNamespace = 'your-hub-namespace';
const resourceGroup = 'your-resource-group';
let notificationHubsClient;

msRestAzure.interactiveLogin().then(credentials => {
  notificationHubsClient = new notificationHubsManagementClient(credentials, subscriptionId);
  notificationHubsClient.notificationHubs
    .list(resourceGroup, notificationHubNamespace)
    .then(notificationHubs => console.log('Retrieved notification hubs: ', notificationHubs));
});
```

## <a name="samples"></a><span data-ttu-id="c7c6d-121">Exemplos</span><span class="sxs-lookup"><span data-stu-id="c7c6d-121">Samples</span></span>

* [<span data-ttu-id="c7c6d-122">Início rápido concluído para Aplicativo Móvel do Serviço de Aplicativo para back-end do Node.js</span><span class="sxs-lookup"><span data-stu-id="c7c6d-122">App Service Mobile completed quickstart for Node.js backend</span></span>](https://azure.microsoft.com/resources/samples/app-service-mobile-nodejs-backend-quickstart/)
* [<span data-ttu-id="c7c6d-123">Anomalias de vibração de tweet detectadas por serviços IoT do Azure em dados de um Intel Edison executando Node.js</span><span class="sxs-lookup"><span data-stu-id="c7c6d-123">Tweet vibration anomalies detected by Azure IoT services on data from an Intel Edison running Node.js</span></span>](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/)

<span data-ttu-id="c7c6d-124">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="c7c6d-124">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
