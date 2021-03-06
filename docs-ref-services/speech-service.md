---
title: SDK de Fala dos Serviços Cognitivos para JavaScript
description: Referência do SDK de Fala dos Serviços Cognitivos para JavaScript
author: mahilleb-msft
ms.author: mahilleb
manager: wolfma
ms.date: 12/18/2018
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: cognitive-services
ms.subservice: speech-service
ms.openlocfilehash: b1375b6beb478cab2475539c03b6bac9f0ea99e0
ms.sourcegitcommit: 34172ad11850839ddd81d02841807e07f3761425
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58052572"
---
# <a name="cognitive-services-speech-sdk-for-javascript"></a>SDK de Fala dos Serviços Cognitivos para JavaScript

## <a name="overview"></a>Visão geral

Para simplificar o desenvolvimento de aplicativos habilitados para fala, a Microsoft fornece o SDK de Fala para uso com o [serviço de Fala](https://aka.ms/csspeech).
O SDK de Fala fornece APIs de Conversão de Fala em Texto e de Tradução de Fala nativas consistentes.

### <a name="install-the-npm-module"></a>Instalar o módulo npm

Instalar o módulo npm do SDK dos Serviços Cognitivos de Fala

```bash
npm install microsoft-cognitiveservices-speech-sdk
```

### <a name="example"></a>Exemplo 

Os trechos de código a seguir mostram como fazer um reconhecimento de fala simples a partir de um arquivo:

```javascript 
// Pull in the required packages.
var sdk = require("microsoft-cognitiveservices-speech-sdk");
var fs = require("fs");

// Replace with your own subscription key, service region (e.g., "westus"), and
// the name of the file you want to run through the speech recognizer.
var subscriptionKey = "YourSubscriptionKey";
var serviceRegion = "YourServiceRegion"; // e.g., "westus"
var filename = "YourAudioFile.wav"; // 16000 Hz, Mono

// Create the push stream we need for the speech sdk.
var pushStream = sdk.AudioInputStream.createPushStream();

// Open the file and push it to the push stream.
fs.createReadStream(filename).on('data', function(arrayBuffer) {
  pushStream.write(arrayBuffer.buffer);
}).on('end', function() {
  pushStream.close();
});

// We are done with the setup
console.log("Now recognizing from: " + filename);

// Create the audio-config pointing to our stream and
// the speech config specifying the language.
var audioConfig = sdk.AudioConfig.fromStreamInput(pushStream);
var speechConfig = sdk.SpeechConfig.fromSubscription(subscriptionKey, serviceRegion);

// Setting the recognition language to English.
speechConfig.speechRecognitionLanguage = "en-US";

// Create the speech recognizer.
var recognizer = new sdk.SpeechRecognizer(speechConfig, audioConfig);

// Start the recognizer and wait for a result.
recognizer.recognizeOnceAsync(
  function (result) {
    console.log(result);

    recognizer.close();
    recognizer = undefined;
  },
  function (err) {
    console.trace("err - " + err);

    recognizer.close();
    recognizer = undefined;
  });
``` 

Confira nossos [inícios rápidos com passo a passo](/azure/cognitive-services/speech-service/quickstart-js-node).

## <a name="samples"></a>Exemplos

* [Guia de início rápido passo a passo para Node.js](/azure/cognitive-services/speech-service/quickstart-js-node).
* [Guia de início rápido passo a passo para o navegador](/azure/cognitive-services/speech-service/quickstart-js-browser).
* Mais exemplos podem ser encontrados em nosso [repositório de exemplo do SDK de Fala](https://aka.ms/csspeech/samples).
