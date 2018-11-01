---
title: Bibliotecas de Grade de Eventos do Azure para Node.js
description: Referência para as bibliotecas de Grade de Eventos do Azure para Node.js
author: rloutlaw
ms.author: routlaw
manager: angerobe
ms.date: 05/03/2018
ms.topic: reference
ms.prod: ''
ms.technology: ''
ms.devlang: nodejs
ms.service: event-grid
ms.custom: devcenter
ms.openlocfilehash: bddf4efc1eda186aee92d30af24125823c7a8f7b
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2018
ms.locfileid: "50339914"
---
# <a name="azure-event-grid-libraries-for-nodejs"></a><span data-ttu-id="26249-103">Bibliotecas de Grade de Eventos do Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="26249-103">Azure Event Grid libraries for Node.js</span></span>

<span data-ttu-id="26249-104">Crie aplicativos orientados para eventos que escutam e reagem a eventos de serviços do Azure e fontes personalizadas usando a manipulação de eventos simples com base em HTTP com a Grade de Eventos do Azure.</span><span class="sxs-lookup"><span data-stu-id="26249-104">Build event-driven applications that listen and react to events from Azure services and custom sources using simple HTTP-based event handling with Azure Event Grid.</span></span>

<span data-ttu-id="26249-105">[Saiba mais](/azure/event-grid/overview) sobre a Grade de Eventos do Azure e começar a usar o [tutorial de eventos do armazenamento de Blobs do Azure](/azure/storage/blobs/storage-blob-event-quickstart).</span><span class="sxs-lookup"><span data-stu-id="26249-105">[Learn more](/azure/event-grid/overview) about Azure Event Grid and get started with the [Azure Blob storage event tutorial](/azure/storage/blobs/storage-blob-event-quickstart).</span></span> 

## <a name="publish-sdk"></a><span data-ttu-id="26249-106">Publicar SDK</span><span class="sxs-lookup"><span data-stu-id="26249-106">Publish SDK</span></span>

<span data-ttu-id="26249-107">Crie eventos, autentique e publique tópicos usando a Grade de Eventos do Azure para publicação de SDK.</span><span class="sxs-lookup"><span data-stu-id="26249-107">Create events, authenticate, and post to topics using the Azure Event Grid publish SDK.</span></span>

### <a name="installation"></a><span data-ttu-id="26249-108">Instalação</span><span class="sxs-lookup"><span data-stu-id="26249-108">Installation</span></span>

<span data-ttu-id="26249-109">Adicione o módulo ao seu projeto com npm:</span><span class="sxs-lookup"><span data-stu-id="26249-109">Add the module to your project with npm:</span></span>

```bash
npm install azure-eventgrid
```

### <a name="example-code"></a><span data-ttu-id="26249-110">Código de exemplo</span><span class="sxs-lookup"><span data-stu-id="26249-110">Example code</span></span>

<span data-ttu-id="26249-111">O segmento de código a seguir publica um evento fictício para um tópico de Grade de Eventos.</span><span class="sxs-lookup"><span data-stu-id="26249-111">The following code segment publishes a mock event to a Event Grid topic.</span></span> <span data-ttu-id="26249-112">Você pode recuperar as chaves de acesso do ponto de extremidade e do tópico do Portal do Azure ou através da CLI do Azure:</span><span class="sxs-lookup"><span data-stu-id="26249-112">You can retrieve the endpoint and topic access keys from the Azure Portal or through the Azure CLI:</span></span>

```azurecli-interactive
endpoint=$(az eventgrid topic show --name <topic_name> -g gridResourceGroup --query "endpoint" --output tsv)
key=$(az eventgrid topic key list --name <topic_name> -g gridResourceGroup --query "key1" --output tsv)
```

```javascript
var EventGridClient = require("azure-eventgrid");
var msRestAzure = require('ms-rest-azure');
var uuid = require('uuid').v4;

let topicCreds = new msRestAzure.TopicCredentials('your-topic-key');
let EGClient = new EventGridClient(topicCreds, 'your-subscription-id');
let topicHostName = 'your-topic-endpoint';
let events = [
   {
   id: uuid(),
   subject: 'TestSubject',
   dataVersion: '1.0',
   eventType: 'Microsoft.MockPublisher.TestEvent',
   data: {
        field1: 'value1',
        filed2: 'value2'
        }
    }
];
return EGClient.publishEvents(topicHostName, events).then((result) => {
   return Promise.resolve(console.log('Published events successfully.'));
 }).catch((err) => {
  console.log('An error ocurred');
  console.dir(err, {depth: null, colors: true});
});
```

<span data-ttu-id="26249-113">Este exemplo mostra como tratar um evento do Armazenamento do Azure:</span><span class="sxs-lookup"><span data-stu-id="26249-113">This sample shows how to handle an event from Azure Storage:</span></span>

```javascript
var http = require('http');

module.exports = function (context, req) {
    context.log('JavaScript HTTP trigger function begun');
    var validationEventType = "Microsoft.EventGrid.SubscriptionValidationEvent";
    var storageBlobCreatedEvent = "Microsoft.Storage.BlobCreated";

    for (var events in req.body) {
        var body = req.body[events];
        // Deserialize the event data into the appropriate type based on event type  
        if (body.data && body.eventType == validationEventType) {
            context.log("Got SubscriptionValidation event data, validation code: " + body.data.validationCode + " topic: " + body.topic);

            // Do any additional validation (as required) and then return back the below response
            var code = body.data.validationCode;
            context.res = { status: 200, body: { "ValidationResponse": code } };
        }

        else if (body.data && body.eventType == storageBlobCreatedEvent) {
            var blobCreatedEventData = body.data;
            context.log("Relaying received blob created event payload:" + JSON.stringify(blobCreatedEventData));
        }
    }
    context.done();
};
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="26249-114">Explorar as APIs de cliente</span><span class="sxs-lookup"><span data-stu-id="26249-114">Explore the client APIs</span></span>](/javascript/api/overview/azure/eventgrid/client)

## <a name="management-sdk"></a><span data-ttu-id="26249-115">SDK de Gerenciamento</span><span class="sxs-lookup"><span data-stu-id="26249-115">Management SDK</span></span>

<span data-ttu-id="26249-116">Crie, atualize ou exclua instâncias da Grade de Eventos, tópicos e assinaturas com o SDK de gerenciamento.</span><span class="sxs-lookup"><span data-stu-id="26249-116">Create, update, or delete Event Grid instances, topics, and subscriptions with the management SDK.</span></span>

### <a name="installation"></a><span data-ttu-id="26249-117">Instalação</span><span class="sxs-lookup"><span data-stu-id="26249-117">Installation</span></span>

```
npm install azure-arm-eventgrid
```

### <a name="example-code"></a><span data-ttu-id="26249-118">Código de exemplo</span><span class="sxs-lookup"><span data-stu-id="26249-118">Example code</span></span>

<span data-ttu-id="26249-119">O código a seguir cria um tópico de Grade de Eventos `topic1` e retorna as chaves de acesso associadas ao tópico recém-criado.</span><span class="sxs-lookup"><span data-stu-id="26249-119">The following code creates an Event Grid topic `topic1` and returns the access keys associated with the newly created topic.</span></span>

```javascript
var msRestAzure = require('ms-rest-azure');
var EventGridManagementClient = require("azure-arm-eventgrid");

msRestAzure.interactiveLogin(function(err, credentials) {
    // Created the management client
    let EGMClient = new EventGridManagementClient(credentials, 'your-subscription-id');
    let topicResponse;
    // created an enventgrid topic
    return EGMClient.topics.createOrUpdate('resourceGroup', 'topic1', { location: 'westus' }).then((topicResponse) => {
        return Promise.resolve(console.log('Created topic ', topicResponse));
    }).then(() => {
        // listed the access keys
        return EGMClient.topics.listSharedAccessKeys('resourceGroup', 'topic1')}
)};
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="26249-120">Explorar as APIs de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="26249-120">Explore the management APIs</span></span>](/javascript/api/overview/azure/eventgrid/management)

## <a name="learn-more"></a><span data-ttu-id="26249-121">Saiba mais</span><span class="sxs-lookup"><span data-stu-id="26249-121">Learn more</span></span>

- [<span data-ttu-id="26249-122">Receber eventos usando o SDK de Grade de Eventos</span><span class="sxs-lookup"><span data-stu-id="26249-122">Receive events using the Event Grid SDK</span></span>](/azure/event-grid/receive-events)
