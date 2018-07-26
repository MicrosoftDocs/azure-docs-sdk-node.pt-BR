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
ms.openlocfilehash: 7941d3850ef6c3518ff0ab13fe1b1ea239ab1828
ms.sourcegitcommit: 99a36d08455760a0436fb6a8fffb542518e3cb2f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/21/2018
ms.locfileid: "39188992"
---
# <a name="javascript-azure-cognitive-services-modules"></a><span data-ttu-id="eba91-103">Módulos de Serviços Cognitivos do Azure para JavaScript</span><span class="sxs-lookup"><span data-stu-id="eba91-103">JavaScript Azure Cognitive Services modules</span></span>

## <a name="vision-modules"></a><span data-ttu-id="eba91-104">Módulos de visão</span><span class="sxs-lookup"><span data-stu-id="eba91-104">Vision modules</span></span>

### <a name="computer-vision"></a><span data-ttu-id="eba91-105">Visual Computacional</span><span class="sxs-lookup"><span data-stu-id="eba91-105">Computer Vision</span></span> 

<span data-ttu-id="eba91-106">Retorna informações sobre o conteúdo visual encontrado em uma imagem:</span><span class="sxs-lookup"><span data-stu-id="eba91-106">Returns information about visual content found in an image:</span></span>

- <span data-ttu-id="eba91-107">Use marcação, descrições e modelos específicos do domínio para identificar o conteúdo e rotulá-lo com segurança.</span><span class="sxs-lookup"><span data-stu-id="eba91-107">Use tagging, descriptions, and domain-specific models to identify content and label it with confidence.</span></span>
- <span data-ttu-id="eba91-108">Aplique configurações de adulto/conteúdo sexual para habilitar restrições automáticas de conteúdo para adultos.</span><span class="sxs-lookup"><span data-stu-id="eba91-108">Apply adult/racy settings to enable automated restriction of adult content.</span></span>
- <span data-ttu-id="eba91-109">Identifique os tipos de imagem e esquemas de cores em fotos.</span><span class="sxs-lookup"><span data-stu-id="eba91-109">Identify image types and color schemes in pictures.</span></span>

<span data-ttu-id="eba91-110">[Experimente o Visual Computacional](https://azure.microsoft.com/services/cognitive-services/computer-vision/) gratuitamente em seu navegador.</span><span class="sxs-lookup"><span data-stu-id="eba91-110">[Try Computer Vision](https://azure.microsoft.com/services/cognitive-services/computer-vision/) for free in your browser.</span></span>

<span data-ttu-id="eba91-111">Obter o módulo de JavaScript com [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span><span class="sxs-lookup"><span data-stu-id="eba91-111">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-computervision
```

<span data-ttu-id="eba91-112">[Saiba mais](/azure/cognitive-services/computer-vision/home) sobre a API da Pesquisa Visual Computacional e comece a usar o [Início rápido do JavaScript para a API da Pesquisa Visual Computacional](/azure/cognitive-services/computer-vision/quickstarts/javascript).</span><span class="sxs-lookup"><span data-stu-id="eba91-112">[Learn more](/azure/cognitive-services/computer-vision/home) about the Computer Vision API and get started with the [Computer Vision API JavaScript quickstart](/azure/cognitive-services/computer-vision/quickstarts/javascript).</span></span>

### <a name="content-moderator"></a><span data-ttu-id="eba91-113">Content Moderator</span><span class="sxs-lookup"><span data-stu-id="eba91-113">Content Moderator</span></span>

<span data-ttu-id="eba91-114">Moderação de texto, vídeo e imagens assistida por computador, aumentada com ferramentas de análise humana.</span><span class="sxs-lookup"><span data-stu-id="eba91-114">Machine-assisted moderation of text, video and images, augmented with human review tools.</span></span>

<span data-ttu-id="eba91-115">Obter o módulo de JavaScript com [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span><span class="sxs-lookup"><span data-stu-id="eba91-115">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-contentmoderator
```

<span data-ttu-id="eba91-116">[Saiba mais](/azure/cognitive-services/content-moderator/overview) sobre o serviço Content Moderator.</span><span class="sxs-lookup"><span data-stu-id="eba91-116">[Learn more](/azure/cognitive-services/content-moderator/overview) about the Content Moderator service.</span></span>

### <a name="face-api"></a><span data-ttu-id="eba91-117">API de Detecção Facial</span><span class="sxs-lookup"><span data-stu-id="eba91-117">Face API</span></span>

<span data-ttu-id="eba91-118">Detecte, identifique, analise, organize e marque rostos em fotos.</span><span class="sxs-lookup"><span data-stu-id="eba91-118">Detect, identify, analyze, organize, and tag faces in photos.</span></span> 

<span data-ttu-id="eba91-119">[Experimente a API de Detecção Facial](https://azure.microsoft.com/services/cognitive-services/face/) em seu navegador.</span><span class="sxs-lookup"><span data-stu-id="eba91-119">[Try the Face API](https://azure.microsoft.com/services/cognitive-services/face/) in your browser.</span></span>

<span data-ttu-id="eba91-120">Obter o módulo de JavaScript com [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span><span class="sxs-lookup"><span data-stu-id="eba91-120">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-face
```

<span data-ttu-id="eba91-121">[Saiba mais](/azure/cognitive-services/face/overview) sobre a API de Detecção Facial e comece a usar o [Início rápido do JavaScript para a API de Detecção Facial](/azure/cognitive-services/Face/quickstarts/javascript).</span><span class="sxs-lookup"><span data-stu-id="eba91-121">[Learn more](/azure/cognitive-services/face/overview) about the Face API and get started with the [Face API JavaScript quickstart](/azure/cognitive-services/Face/quickstarts/javascript).</span></span>

## <a name="search-modules"></a><span data-ttu-id="eba91-122">Módulos de pesquisa</span><span class="sxs-lookup"><span data-stu-id="eba91-122">Search modules</span></span>

### <a name="web-search"></a><span data-ttu-id="eba91-123">Pesquisa na Web</span><span class="sxs-lookup"><span data-stu-id="eba91-123">Web search</span></span>

<span data-ttu-id="eba91-124">Recupere documentos da Web indexados pela API de Pesquisa na Web do Bing e restrinja os resultados por tipo de resultado, atualização e muito mais.</span><span class="sxs-lookup"><span data-stu-id="eba91-124">Retrieve web documents indexed by the Bing Web Search API and narrow down the results by result type, freshness and more.</span></span> 

<span data-ttu-id="eba91-125">[Experimente a API de Pesquisa na Web](https://azure.microsoft.com/services/cognitive-services/bing-web-search-api/) em seu navegador.</span><span class="sxs-lookup"><span data-stu-id="eba91-125">[Try the Web Search API](https://azure.microsoft.com/services/cognitive-services/bing-web-search-api/) in your browser.</span></span>

<span data-ttu-id="eba91-126">Obter o módulo de JavaScript com [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span><span class="sxs-lookup"><span data-stu-id="eba91-126">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-websearch
```

<span data-ttu-id="eba91-127">[Saiba mais](/azure/cognitive-services/bing-web-search/overview) sobre a API de Pesquisa na Web do Bing e comece a usar o [Início rápido do Node.js para a API de Pesquisa na Web](/azure/cognitive-services/bing-web-search/quickstarts/nodejs).</span><span class="sxs-lookup"><span data-stu-id="eba91-127">[Learn more](/azure/cognitive-services/bing-web-search/overview) about the Bing Web Search API and get started with the [Web Search API Node.js quickstart](/azure/cognitive-services/bing-web-search/quickstarts/nodejs).</span></span>

### <a name="image-search"></a><span data-ttu-id="eba91-128">Pesquisa de imagem</span><span class="sxs-lookup"><span data-stu-id="eba91-128">Image search</span></span>

<span data-ttu-id="eba91-129">Pesquise imagens e obtenha miniaturas, URLs de imagem completa, metadados de imagem e muito mais em seus resultados.</span><span class="sxs-lookup"><span data-stu-id="eba91-129">Search for images and get thumbnails, full image URLs, image metadata and more in your results.</span></span>

<span data-ttu-id="eba91-130">[Experimente a API de Pesquisa de Imagem](https://azure.microsoft.com/services/cognitive-services/bing-image-search-api/) em seu navegador.</span><span class="sxs-lookup"><span data-stu-id="eba91-130">[Try the Image Search API](https://azure.microsoft.com/services/cognitive-services/bing-image-search-api/) in your browser.</span></span>

<span data-ttu-id="eba91-131">Obter o módulo de JavaScript com [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span><span class="sxs-lookup"><span data-stu-id="eba91-131">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-imagesearch
```

<span data-ttu-id="eba91-132">[Saiba mais](/azure/cognitive-services/bing-image-search/overview) sobre a API de Pesquisa de Imagem do Bing e comece a usar o [Início rápido do Node.js para a API de Pesquisa de Imagem do Bing](/azure/cognitive-services/bing-image-search/quickstarts/nodejs).</span><span class="sxs-lookup"><span data-stu-id="eba91-132">[Learn more](/azure/cognitive-services/bing-image-search/overview) about the Bing Image Search API and get started with the [Image Search API Node.js quickstart](/azure/cognitive-services/bing-image-search/quickstarts/nodejs).</span></span>


### <a name="entity-search"></a><span data-ttu-id="eba91-133">Pesquisa de entidade</span><span class="sxs-lookup"><span data-stu-id="eba91-133">Entity search</span></span>

<span data-ttu-id="eba91-134">Pesquise a entidade mais relevante (local, pessoa ou coisa) para determinado termo de pesquisa ou local.</span><span class="sxs-lookup"><span data-stu-id="eba91-134">Search for the most relevant entity (place, person, or thing) for a given search term or location.</span></span>

<span data-ttu-id="eba91-135">[Experimente a API de Pesquisa de Entidade](https://azure.microsoft.com/services/cognitive-services/bing-entity-search-api/) em seu navegador.</span><span class="sxs-lookup"><span data-stu-id="eba91-135">[Try the Entity Search API](https://azure.microsoft.com/services/cognitive-services/bing-entity-search-api/) in your browser.</span></span>

<span data-ttu-id="eba91-136">Obter o módulo de JavaScript com [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span><span class="sxs-lookup"><span data-stu-id="eba91-136">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-entitysearch
```

<span data-ttu-id="eba91-137">[Saiba mais](/azure/cognitive-services/bing-entities-search/search-the-web) sobre a API de Pesquisa de Entidade do Bing e comece a usar o [Início rápido do Node.js para a API de Pesquisa de Entidade do Bing](/azure/cognitive-services/bing-entities-search/quickstarts/nodejs).</span><span class="sxs-lookup"><span data-stu-id="eba91-137">[Learn more](/azure/cognitive-services/bing-entities-search/search-the-web) about the Bing Entity Search API and get started with the [Entity Search API Node.js quickstart](/azure/cognitive-services/bing-entities-search/quickstarts/nodejs).</span></span>

### <a name="custom-search"></a><span data-ttu-id="eba91-138">Pesquisa personalizada</span><span class="sxs-lookup"><span data-stu-id="eba91-138">Custom search</span></span>

<span data-ttu-id="eba91-139">Compile e personalize uma pesquisa na Web que atenda a seu domínio de pesquisa específico.</span><span class="sxs-lookup"><span data-stu-id="eba91-139">Build and a custom web search that meets your specific search domain.</span></span>

<span data-ttu-id="eba91-140">Obter o módulo de JavaScript com [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span><span class="sxs-lookup"><span data-stu-id="eba91-140">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-customsearch
```

<span data-ttu-id="eba91-141">[Saiba mais](/azure/cognitive-services/bing-custom-search/) sobre o serviço de Pesquisa Personalizada do Bing e comece a trabalhar com a consulta de sua pesquisa personalizada nos seus aplicativos com o [Início rápido do Node.js para API de Pesquisa Personalizada](/azure/cognitive-services/bing-custom-search/call-endpoint-nodejs).</span><span class="sxs-lookup"><span data-stu-id="eba91-141">[Learn more](/azure/cognitive-services/bing-custom-search/) about the Bing Custom Search service and get started with querying your custom search from your apps with the [Custom Search API Node.js quickstart](/azure/cognitive-services/bing-custom-search/call-endpoint-nodejs).</span></span>

### <a name="video-search"></a><span data-ttu-id="eba91-142">Pesquisa de vídeo</span><span class="sxs-lookup"><span data-stu-id="eba91-142">Video search</span></span>

<span data-ttu-id="eba91-143">Encontre vídeos na Web, obtenha resultados com o criador, codificação, duração, e exiba os metadados de contagem.</span><span class="sxs-lookup"><span data-stu-id="eba91-143">Find videos across the web and get results with creator, encoding, length, and view count metadata.</span></span>

<span data-ttu-id="eba91-144">[Experimente a API de Pesquisa de Vídeo](https://azure.microsoft.com/services/cognitive-services/bing-video-search-api/) em seu navegador.</span><span class="sxs-lookup"><span data-stu-id="eba91-144">[Try the Video Search API](https://azure.microsoft.com/services/cognitive-services/bing-video-search-api/) in your browser.</span></span>

<span data-ttu-id="eba91-145">Obter o módulo de JavaScript com [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span><span class="sxs-lookup"><span data-stu-id="eba91-145">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-videosearch
```

<span data-ttu-id="eba91-146">[Saiba mais](/azure/cognitive-services/bing-video-search/search-the-web) sobre o serviço de Pesquisa de Vídeo do Bing e comece a usar o [Início rápido do Node.js para a API de Pesquisa de Vídeo](/azure/cognitive-services/bing-video-search/nodejs).</span><span class="sxs-lookup"><span data-stu-id="eba91-146">[Learn more](/azure/cognitive-services/bing-video-search/search-the-web) about the Bing Video Search service and get started with the [Video Search API Node.js quickstart](/azure/cognitive-services/bing-video-search/nodejs).</span></span>


### <a name="news-search"></a><span data-ttu-id="eba91-147">Pesquisa de notícias</span><span class="sxs-lookup"><span data-stu-id="eba91-147">News search</span></span>

<span data-ttu-id="eba91-148">Pesquise na Web artigos de notícias e trabalhe com o artigo, notícias relacionadas, imagens e metadados de informações do provedor.</span><span class="sxs-lookup"><span data-stu-id="eba91-148">Search the web for news articles and work with article, related news, images, and provider info metadata.</span></span>

<span data-ttu-id="eba91-149">[Experimente a API de Pesquisa de Notícias](https://azure.microsoft.com/services/cognitive-services/bing-news-search-api/) em seu navegador.</span><span class="sxs-lookup"><span data-stu-id="eba91-149">[Try the News Search API](https://azure.microsoft.com/services/cognitive-services/bing-news-search-api/) in your browser.</span></span>

<span data-ttu-id="eba91-150">Obter o módulo de JavaScript com [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span><span class="sxs-lookup"><span data-stu-id="eba91-150">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-newssearch
```

<span data-ttu-id="eba91-151">[Saiba mais](/azure/cognitive-services/bing-news-search/search-the-web) sobre o serviço de Pesquisa de Notícias do Bing e comece a usar o [Início rápido do JavaScript para a API de Pesquisa de Notícias](/azure/cognitive-services/bing-news-search/nodejs).</span><span class="sxs-lookup"><span data-stu-id="eba91-151">[Learn more](/azure/cognitive-services/bing-news-search/search-the-web) about the Bing News Search service and get started with the [News Search API JavaScript quickstart](/azure/cognitive-services/bing-news-search/nodejs).</span></span>


## <a name="language-modules"></a><span data-ttu-id="eba91-152">Módulos de linguagem</span><span class="sxs-lookup"><span data-stu-id="eba91-152">Language modules</span></span>

### <a name="text-analytics"></a><span data-ttu-id="eba91-153">Análise de texto</span><span class="sxs-lookup"><span data-stu-id="eba91-153">Text Analytics</span></span> 

<span data-ttu-id="eba91-154">A API de Análise de Texto é um serviço baseado em nuvem que fornece processamento de texto natural em torno de texto bruto.</span><span class="sxs-lookup"><span data-stu-id="eba91-154">The Text Analytics API is a cloud-based service that provides  natural language processing over raw text.</span></span> <span data-ttu-id="eba91-155">A API inclui três funções principais:</span><span class="sxs-lookup"><span data-stu-id="eba91-155">The API includes three main functions:</span></span>

- <span data-ttu-id="eba91-156">Análise de sentimento</span><span class="sxs-lookup"><span data-stu-id="eba91-156">Sentiment analysis</span></span>
- <span data-ttu-id="eba91-157">Extração de frases-chave</span><span class="sxs-lookup"><span data-stu-id="eba91-157">Key phrase extraction</span></span>
- <span data-ttu-id="eba91-158">Detecção de idioma</span><span class="sxs-lookup"><span data-stu-id="eba91-158">Language detection</span></span>

<span data-ttu-id="eba91-159">[Experimente a API de Análise de Texto](https://azure.microsoft.com/services/cognitive-services/text-analytics/) em seu navegador.</span><span class="sxs-lookup"><span data-stu-id="eba91-159">[Try the Text Analytics API](https://azure.microsoft.com/services/cognitive-services/text-analytics/) in your browser.</span></span>

<span data-ttu-id="eba91-160">Obter o módulo de JavaScript com [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span><span class="sxs-lookup"><span data-stu-id="eba91-160">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-textanalytics
```

<span data-ttu-id="eba91-161">[Saiba mais](/azure/cognitive-services/text-analytics/overview) sobre a API de Análise de Texto e comece a usar o [Início rápido do Node.js para a API de Análise de Texto](/azure/cognitive-services/text-analytics/quickstarts/nodejs).</span><span class="sxs-lookup"><span data-stu-id="eba91-161">[Learn more](/azure/cognitive-services/text-analytics/overview) about the Text Analytics API and get started with the [Text Analytics API Node.js quickstart](/azure/cognitive-services/text-analytics/quickstarts/nodejs).</span></span>


### <a name="spell-check"></a><span data-ttu-id="eba91-162">Verificação ortográfica</span><span class="sxs-lookup"><span data-stu-id="eba91-162">Spell Check</span></span>

<span data-ttu-id="eba91-163">Faça verificações da gramática contextual e ortográfica com a API de Verificação Ortográfica do Bing.</span><span class="sxs-lookup"><span data-stu-id="eba91-163">Perform contextual grammar and spell checking with the Bing Spell Check API.</span></span>

<span data-ttu-id="eba91-164">[Experimente a API de Verificação Ortográfica](https://azure.microsoft.com/services/cognitive-services/spell-check/) em seu navegador.</span><span class="sxs-lookup"><span data-stu-id="eba91-164">[Try the Spell Check API](https://azure.microsoft.com/services/cognitive-services/spell-check/) in your browser.</span></span>

<span data-ttu-id="eba91-165">Obter o módulo de JavaScript com [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span><span class="sxs-lookup"><span data-stu-id="eba91-165">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-spellcheck
```

<span data-ttu-id="eba91-166">[Saiba mais](/azure/cognitive-services/bing-spell-check/proof-text) sobre a API de Verificação Ortográfica e comece a usar o [Início rápido do Node.js para API de Verificação Ortográfica](/azure/cognitive-services/bing-spell-check/quickstarts/nodejs).</span><span class="sxs-lookup"><span data-stu-id="eba91-166">[Learn more](/azure/cognitive-services/bing-spell-check/proof-text) about the Spell Check API and get started with the [Spell Check API Node.js quickstart](/azure/cognitive-services/bing-spell-check/quickstarts/nodejs).</span></span>

## <a name="samples"></a><span data-ttu-id="eba91-167">Exemplos</span><span class="sxs-lookup"><span data-stu-id="eba91-167">Samples</span></span>

<span data-ttu-id="eba91-168">Explore mais [códigos Node.js de exemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que você pode usar em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="eba91-168">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
