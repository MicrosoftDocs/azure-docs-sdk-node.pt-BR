---
title: Módulos de Serviços Cognitivos do Azure para Node.js
description: Referência dos módulos de Serviços cognitivos do Azure para Node.js
author: brapel
ms.author: v-brapel
manager: ehansen
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Cognitive Services
ms.openlocfilehash: fb0319965f7ea9d1bcab25e0e213998052b78ae0
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/08/2018
ms.locfileid: "51071856"
---
# <a name="javascript-azure-cognitive-services-modules"></a>Módulos de Serviços Cognitivos do Azure para JavaScript

## <a name="vision-modules"></a>Módulos de visão

### <a name="computer-vision"></a>Visual Computacional 

Retorna informações sobre o conteúdo visual encontrado em uma imagem:

- Use marcação, descrições e modelos específicos do domínio para identificar o conteúdo e rotulá-lo com segurança.
- Aplique configurações de adulto/conteúdo sexual para habilitar restrições automáticas de conteúdo para adultos.
- Identifique os tipos de imagem e esquemas de cores em fotos.

[Experimente o Visual Computacional](https://azure.microsoft.com/services/cognitive-services/computer-vision/) gratuitamente em seu navegador.

Obter o módulo de JavaScript com [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):

```
npm install azure-cognitiveservices-computervision
```

[Saiba mais](/azure/cognitive-services/computer-vision/home) sobre a API da Pesquisa Visual Computacional e comece a usar o [Início rápido do JavaScript para a API da Pesquisa Visual Computacional](/azure/cognitive-services/computer-vision/quickstarts/javascript).

### <a name="content-moderator"></a>Content Moderator

Moderação de texto, vídeo e imagens assistida por computador, aumentada com ferramentas de análise humana.

Obter o módulo de JavaScript com [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):

```
npm install azure-cognitiveservices-contentmoderator
```

[Saiba mais](/azure/cognitive-services/content-moderator/overview) sobre o serviço Content Moderator.

### <a name="face-api"></a>API de Detecção Facial

Detecte, identifique, analise, organize e marque rostos em fotos. 

[Experimente a API de Detecção Facial](https://azure.microsoft.com/services/cognitive-services/face/) em seu navegador.

Obter o módulo de JavaScript com [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):

```
npm install azure-cognitiveservices-face
```

[Saiba mais](/azure/cognitive-services/face/overview) sobre a API de Detecção Facial e comece a usar o [Início rápido do JavaScript para a API de Detecção Facial](/azure/cognitive-services/Face/quickstarts/javascript).

## <a name="search-modules"></a>Módulos de pesquisa

### <a name="web-search"></a>Pesquisa na Web

Recupere documentos da Web indexados pela API de Pesquisa na Web do Bing e restrinja os resultados por tipo de resultado, atualização e muito mais. 

[Experimente a API de Pesquisa na Web](https://azure.microsoft.com/services/cognitive-services/bing-web-search-api/) em seu navegador.

Obter o módulo de JavaScript com [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):

```
npm install azure-cognitiveservices-websearch
```

[Saiba mais](/azure/cognitive-services/bing-web-search/overview) sobre a API de Pesquisa na Web do Bing e comece a usar o [Início rápido do Node.js para a API de Pesquisa na Web](/azure/cognitive-services/bing-web-search/quickstarts/nodejs).

### <a name="image-search"></a>Pesquisa de imagem

Pesquise imagens e obtenha miniaturas, URLs de imagem completa, metadados de imagem e muito mais em seus resultados.

[Experimente a API de Pesquisa de Imagem](https://azure.microsoft.com/services/cognitive-services/bing-image-search-api/) em seu navegador.

Obter o módulo de JavaScript com [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):

```
npm install azure-cognitiveservices-imagesearch
```

[Saiba mais](/azure/cognitive-services/bing-image-search/overview) sobre a API de Pesquisa de Imagem do Bing e comece a usar o [Início rápido do Node.js para a API de Pesquisa de Imagem do Bing](/azure/cognitive-services/bing-image-search/quickstarts/nodejs).


### <a name="entity-search"></a>Pesquisa de entidade

Pesquise a entidade mais relevante (local, pessoa ou coisa) para determinado termo de pesquisa ou local.

[Experimente a API de Pesquisa de Entidade](https://azure.microsoft.com/services/cognitive-services/bing-entity-search-api/) em seu navegador.

Obter o módulo de JavaScript com [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):

```
npm install azure-cognitiveservices-entitysearch
```

[Saiba mais](/azure/cognitive-services/bing-entities-search/search-the-web) sobre a API de Pesquisa de Entidade do Bing e comece a usar o [Início rápido do Node.js para a API de Pesquisa de Entidade do Bing](/azure/cognitive-services/bing-entities-search/quickstarts/nodejs).

### <a name="custom-search"></a>Pesquisa personalizada

Compile e personalize uma pesquisa na Web que atenda a seu domínio de pesquisa específico.

Obter o módulo de JavaScript com [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):

```
npm install azure-cognitiveservices-customsearch
```

[Saiba mais](/azure/cognitive-services/bing-custom-search/) sobre o serviço de Pesquisa Personalizada do Bing e comece a trabalhar com a consulta de sua pesquisa personalizada nos seus aplicativos com o [Início rápido do Node.js para API de Pesquisa Personalizada](/azure/cognitive-services/bing-custom-search/call-endpoint-nodejs).

### <a name="video-search"></a>Pesquisa de vídeo

Encontre vídeos na Web, obtenha resultados com o criador, codificação, duração, e exiba os metadados de contagem.

[Experimente a API de Pesquisa de Vídeo](https://azure.microsoft.com/services/cognitive-services/bing-video-search-api/) em seu navegador.

Obter o módulo de JavaScript com [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):

```
npm install azure-cognitiveservices-videosearch
```

[Saiba mais](/azure/cognitive-services/bing-video-search/search-the-web) sobre o serviço de Pesquisa de Vídeo do Bing e comece a usar o [Início rápido do Node.js para a API de Pesquisa de Vídeo](/azure/cognitive-services/bing-video-search/nodejs).


### <a name="news-search"></a>Pesquisa de notícias

Pesquise na Web artigos de notícias e trabalhe com o artigo, notícias relacionadas, imagens e metadados de informações do provedor.

[Experimente a API de Pesquisa de Notícias](https://azure.microsoft.com/services/cognitive-services/bing-news-search-api/) em seu navegador.

Obter o módulo de JavaScript com [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):

```
npm install azure-cognitiveservices-newssearch
```

[Saiba mais](/azure/cognitive-services/bing-news-search/search-the-web) sobre o serviço de Pesquisa de Notícias do Bing e comece a usar o [Início rápido do JavaScript para a API de Pesquisa de Notícias](/azure/cognitive-services/bing-news-search/nodejs).


## <a name="language-modules"></a>Módulos de linguagem

### <a name="text-analytics"></a>Análise de texto 

A API de Análise de Texto é um serviço baseado em nuvem que fornece processamento de texto natural em torno de texto bruto. A API inclui três funções principais:

- Análise de sentimento
- Extração de frases-chave
- Detecção de idioma

[Experimente a API de Análise de Texto](https://azure.microsoft.com/services/cognitive-services/text-analytics/) em seu navegador.

Obter o módulo de JavaScript com [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):

```
npm install azure-cognitiveservices-textanalytics
```

[Saiba mais](/azure/cognitive-services/text-analytics/overview) sobre a API de Análise de Texto e comece a usar o [Início rápido do Node.js para a API de Análise de Texto](/azure/cognitive-services/text-analytics/quickstarts/nodejs).


### <a name="spell-check"></a>Verificação ortográfica

Faça verificações da gramática contextual e ortográfica com a API de Verificação Ortográfica do Bing.

[Experimente a API de Verificação Ortográfica](https://azure.microsoft.com/services/cognitive-services/spell-check/) em seu navegador.

Obter o módulo de JavaScript com [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):

```
npm install azure-cognitiveservices-spellcheck
```

[Saiba mais](/azure/cognitive-services/bing-spell-check/proof-text) sobre a API de Verificação Ortográfica e comece a usar o [Início rápido do Node.js para API de Verificação Ortográfica](/azure/cognitive-services/bing-spell-check/quickstarts/nodejs).

## <a name="samples"></a>Exemplos

Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.
