---
title: SDK de Fala dos Serviços Cognitivos para JavaScript
description: Referência do SDK de Fala dos Serviços Cognitivos para JavaScript
author: mahilleb-msft
ms.author: mahilleb
manager: wolfma
ms.date: 09/24/2018
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: cognitive-services
ms.component: speech-service
ms.openlocfilehash: 69167faa5b2677fc15561ed33beccf7925efbe39
ms.sourcegitcommit: 7cea63cdde5fcfb19271bf7a93b1eb0dabdddb31
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2018
ms.locfileid: "49724411"
---
# <a name="cognitive-services-speech-sdk-for-javascript"></a>SDK de Fala dos Serviços Cognitivos para JavaScript

## <a name="overview"></a>Visão geral

Para simplificar o desenvolvimento de aplicativos habilitados para fala, a Microsoft fornece o SDK de Fala para uso com o [serviço de Fala](https://aka.ms/csspeech).
O SDK de Fala fornece APIs de Conversão de Fala em Texto e de Tradução de Fala nativas consistentes.

> [!NOTE]
> O SDK de Fala dos serviços Cognitivos está disponível atualmente apenas para navegadores.
> Um pacote NPM sairá em breve.

### <a name="install-the-speech-sdk"></a>Instalar o SDK de Fala

Baixe o SDK de Fala como um [pacote.zip](https://aka.ms/csspeech/jsbrowserpackage) e descompacte-o.
Isso deve desempacotar vários arquivos, incluindo um arquivo chamado `microsoft.cognitiveservices.speech.sdk.bundle.js`.
Carregue esse arquivo como um recurso de script em sua página da Web para começar a usar o SDK de Fala:

```html
<script src="microsoft.cognitiveservices.speech.sdk.bundle.js"></script>
```

### <a name="example"></a>Exemplo 

Os trechos de código abaixo ilustram como fazer um reconhecimento de fala simples em seu navegador:

```javascript 
var SpeechSDK = window.SpeechSDK;
var speechConfig = SpeechSDK.SpeechConfig.fromSubscription("your-subscription-key", "your-service-region");
speechConfig.language = "en-US";
var audioConfig = SpeechSDK.AudioConfig.fromDefaultMicrophoneInput();
recognizer = new SpeechSDK.SpeechRecognizer(speechConfig, audioConfig);

recognizer.recognizeOnceAsync(
  function (result) {
    alert("Recognition result:" + JSON.stringify(result));
    recognizer.close();
  },
  function (err) {
    alert("An error occurred:" + JSON.stringify(err));
    recognizer.close();
  }
);
``` 

Confira nossos [inícios rápidos com passo a passo](/azure/cognitive-services/speech-service/quickstart-js-browser).

## <a name="samples"></a>Exemplos

Explorar mais exemplos em nosso [repositório de exemplo do SDK de Fala](https://aka.ms/csspeech/samples).
