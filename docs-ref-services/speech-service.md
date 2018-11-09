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
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/08/2018
ms.locfileid: "51134227"
---
# <a name="cognitive-services-speech-sdk-for-javascript"></a><span data-ttu-id="6e737-103">SDK de Fala dos Serviços Cognitivos para JavaScript</span><span class="sxs-lookup"><span data-stu-id="6e737-103">Cognitive Services Speech SDK for JavaScript</span></span>

## <a name="overview"></a><span data-ttu-id="6e737-104">Visão geral</span><span class="sxs-lookup"><span data-stu-id="6e737-104">Overview</span></span>

<span data-ttu-id="6e737-105">Para simplificar o desenvolvimento de aplicativos habilitados para fala, a Microsoft fornece o SDK de Fala para uso com o [serviço de Fala](https://aka.ms/csspeech).</span><span class="sxs-lookup"><span data-stu-id="6e737-105">To simplify the development of speech-enabled applications, Microsoft provides the Speech SDK for use with the [Speech service](https://aka.ms/csspeech).</span></span>
<span data-ttu-id="6e737-106">O SDK de Fala fornece APIs de Conversão de Fala em Texto e de Tradução de Fala nativas consistentes.</span><span class="sxs-lookup"><span data-stu-id="6e737-106">The Speech SDK provides consistent native Speech-to-Text and Speech Translation APIs.</span></span>

> [!NOTE]
> <span data-ttu-id="6e737-107">O SDK de Fala dos serviços Cognitivos está disponível atualmente apenas para navegadores.</span><span class="sxs-lookup"><span data-stu-id="6e737-107">The Cognitive Services Speech SDK is currently available only for browsers.</span></span>
> <span data-ttu-id="6e737-108">Um pacote NPM sairá em breve.</span><span class="sxs-lookup"><span data-stu-id="6e737-108">An NPM package will follow soon.</span></span>

### <a name="install-the-speech-sdk"></a><span data-ttu-id="6e737-109">Instalar o SDK de Fala</span><span class="sxs-lookup"><span data-stu-id="6e737-109">Install the Speech SDK</span></span>

<span data-ttu-id="6e737-110">Baixe o SDK de Fala como um [pacote.zip](https://aka.ms/csspeech/jsbrowserpackage) e descompacte-o.</span><span class="sxs-lookup"><span data-stu-id="6e737-110">Download the Speech SDK as a [.zip package](https://aka.ms/csspeech/jsbrowserpackage) and unpack it.</span></span>
<span data-ttu-id="6e737-111">Isso deve desempacotar vários arquivos, incluindo um arquivo chamado `microsoft.cognitiveservices.speech.sdk.bundle.js`.</span><span class="sxs-lookup"><span data-stu-id="6e737-111">This should result in a number of files being unpacked including a file named `microsoft.cognitiveservices.speech.sdk.bundle.js`.</span></span>
<span data-ttu-id="6e737-112">Carregue esse arquivo como um recurso de script em sua página da Web para começar a usar o SDK de Fala:</span><span class="sxs-lookup"><span data-stu-id="6e737-112">Load this file as a script resource in your web page to start using the Speech SDK:</span></span>

```html
<script src="microsoft.cognitiveservices.speech.sdk.bundle.js"></script>
```

### <a name="example"></a><span data-ttu-id="6e737-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6e737-113">Example</span></span> 

<span data-ttu-id="6e737-114">Os trechos de código abaixo ilustram como fazer um reconhecimento de fala simples em seu navegador:</span><span class="sxs-lookup"><span data-stu-id="6e737-114">The following code snippets illustrates how to do simple speech recognition from your browser:</span></span>

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

<span data-ttu-id="6e737-115">Confira nossos [inícios rápidos com passo a passo](/azure/cognitive-services/speech-service/quickstart-js-browser).</span><span class="sxs-lookup"><span data-stu-id="6e737-115">Check out our [step-by-step quickstart](/azure/cognitive-services/speech-service/quickstart-js-browser).</span></span>

## <a name="samples"></a><span data-ttu-id="6e737-116">Exemplos</span><span class="sxs-lookup"><span data-stu-id="6e737-116">Samples</span></span>

<span data-ttu-id="6e737-117">Explorar mais exemplos em nosso [repositório de exemplo do SDK de Fala](https://aka.ms/csspeech/samples).</span><span class="sxs-lookup"><span data-stu-id="6e737-117">Explore more samples in our [Speech SDK sample repository](https://aka.ms/csspeech/samples).</span></span>
