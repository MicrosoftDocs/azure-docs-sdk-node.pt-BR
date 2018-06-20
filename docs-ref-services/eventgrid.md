---
title: Bibliotecas de Grade de Eventos do Azure para Node.js
description: Referência para as bibliotecas de Grade de Eventos do Azure para Node.js
author: rloutlaw
ms.author: routlaw
manager: angerobe
ms.date: 05/03/2018
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: event-grid
ms.custom: devcenter
ms.openlocfilehash: 165845f0c94b4e6fd0f385f2262903e44845d09a
ms.sourcegitcommit: b4cf45cb23da56718b482cf7fc240c592e15206b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33849949"
---
# <a name="azure-event-grid-libraries-for-nodejs"></a>Bibliotecas de Grade de Eventos do Azure para Node.js

Crie aplicativos orientados para eventos que escutam e reagem a eventos de serviços do Azure e fontes personalizadas usando a manipulação de eventos simples com base em HTTP com a Grade de Eventos do Azure.

[Saiba mais](/azure/event-grid/overview) sobre a Grade de Eventos do Azure e começar a usar o [tutorial de eventos do armazenamento de Blobs do Azure](/azure/storage/blobs/storage-blob-event-quickstart). 

## <a name="publish-sdk"></a>Publicar SDK

Crie eventos, autentique e publique tópicos usando a Grade de Eventos do Azure para publicação de SDK.

### <a name="installation"></a>Instalação

Adicione o módulo ao seu projeto com npm:

```bash
npm install azure-eventgrid
```

### <a name="example-code"></a>Código de exemplo

O segmento de código a seguir publica um evento fictício para um tópico de Grade de Eventos. Você pode recuperar as chaves de acesso do ponto de extremidade e do tópico do Portal do Azure ou através da CLI do Azure:

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

Este exemplo mostra como tratar um evento do Armazenamento do Azure:

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
> [Explorar as APIs de cliente](/javascript/api/overview/azure/eventgrid/client)

## <a name="management-sdk"></a>SDK de Gerenciamento

Crie, atualize ou exclua instâncias da Grade de Eventos, tópicos e assinaturas com o SDK de gerenciamento.

### <a name="installation"></a>Instalação

```
npm install azure-arm-eventgrid
```

### <a name="example-code"></a>Código de exemplo

O código a seguir cria um tópico de Grade de Eventos `topic1` e retorna as chaves de acesso associadas ao tópico recém-criado.

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
> [Explorar as APIs de gerenciamento](/javascript/api/overview/azure/eventgrid/management)

## <a name="learn-more"></a>Saiba mais

- [Receber eventos usando o SDK de Grade de Eventos](/azure/event-grid/receive-events)