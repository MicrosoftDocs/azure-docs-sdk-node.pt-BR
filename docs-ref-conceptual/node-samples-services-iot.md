---
title: "Sistema de mensagens do Azure e IoT com exemplos de código do Node.js"
description: "Código de exemplo que demonstra como usar o sistema de mensagens do Azure e a IoT com Node.js"
author: craigshoemaker
manager: routlaw
ms.devlang: nodejs
ms.topic: article
ms.service: azure-nodejs
ms.date: 06/17/2017
ms.author: cshoe
ms.openlocfilehash: 45aad90670a8ac8c0f32f9deab2eb32043c52d96
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/26/2018
---
# <a name="sample-code-for-using-azure-messaging-and-iot-with-nodejs"></a><span data-ttu-id="b64b7-103">Código de exemplo para usar o sistema de mensagens do Azure e a IoT com Node.js</span><span class="sxs-lookup"><span data-stu-id="b64b7-103">Sample code for using Azure messaging and IoT with Node.js</span></span>

<span data-ttu-id="b64b7-104">O código de exemplo a seguir ilustra como usar o sistema de mensagens do Azure e a IoT com Node.js.</span><span class="sxs-lookup"><span data-stu-id="b64b7-104">The following sample code illustrates using Azure messaging and IoT with Node.js</span></span>

<span data-ttu-id="b64b7-105">Se você precisar de código para outras tarefas, poderá procurar na lista completa de [exemplos do Node.js do Azure](https://azure.microsoft.com/resources/samples/?term=nodejs).</span><span class="sxs-lookup"><span data-stu-id="b64b7-105">If you need code for other tasks, you can browse the full list of [Azure Node.js samples](https://azure.microsoft.com/resources/samples/?term=nodejs).</span></span>

| | |
|---|---|
| <span data-ttu-id="b64b7-106">**Hub do Azure IoT**</span><span class="sxs-lookup"><span data-stu-id="b64b7-106">**Azure IoT Hub**</span></span> ||
| [<span data-ttu-id="b64b7-107">Ping no Hub do Azure IoT</span><span class="sxs-lookup"><span data-stu-id="b64b7-107">Azure IoT Hub ping</span></span>](https://github.com/Azure-Samples/iot-hub-node-ping) | <span data-ttu-id="b64b7-108">Solução de ping simples para ajudar a validar uma conectividade do dispositivo com o Azure IoT Hub.</span><span class="sxs-lookup"><span data-stu-id="b64b7-108">Simple ping solution to help validate a device connectivity to Azure IoT Hub.</span></span> |
| [<span data-ttu-id="b64b7-109">Anomalias de vibração de tweet detectadas por serviços IoT do Azure em dados de um Intel Edison executando Node.js</span><span class="sxs-lookup"><span data-stu-id="b64b7-109">Tweet vibration anomalies detected by Azure IoT services on data from an Intel Edison running Node.js</span></span>](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/) | <span data-ttu-id="b64b7-110">Projeto de IoT que usa o Hub do Azure IoT e mostra um dispositivo que executa o nó para enviar dados de telemetria e que é analisado pelos serviços do Azure IoT.</span><span class="sxs-lookup"><span data-stu-id="b64b7-110">IoT project using Azure IoT Hub and showing a device running node to send telemetry data and that is analyzed by Azure IoT services.</span></span> |
| <span data-ttu-id="b64b7-111">**IoT para Intel Edison**</span><span class="sxs-lookup"><span data-stu-id="b64b7-111">**Intel Edison IoT**</span></span> ||
| [<span data-ttu-id="b64b7-112">Introdução ao Kit de Início do Azure IoT para Intel Edison</span><span class="sxs-lookup"><span data-stu-id="b64b7-112">Get started with Intel Edison Azure IoT Starter Kit</span></span>](https://github.com/Azure-Samples/iot-hub-node-intel-edison-getstartedkit) | <span data-ttu-id="b64b7-113">Demonstra como o Azure IoT usa o Kit de Início do Azure IoT – Edison Intel.</span><span class="sxs-lookup"><span data-stu-id="b64b7-113">Demonstrates Azure IoT using the Azure IoT Starter Kit - Intel Edison.</span></span> |
| <span data-ttu-id="b64b7-114">**MQTT**</span><span class="sxs-lookup"><span data-stu-id="b64b7-114">**MQTT**</span></span> ||
| [<span data-ttu-id="b64b7-115">Módulos de exemplo de Gateway MQTT e HTTP</span><span class="sxs-lookup"><span data-stu-id="b64b7-115">Sample MQTT and HTTP Gateway modules</span></span>](https://github.com/Azure-Samples/iot-gateway-mqtt-http) | <span data-ttu-id="b64b7-116">Fornece dois módulos de Gateway que expõem os pontos de extremidade MQTT e HTTPS no estilo IoTHub para upoad de telemetria e, no caso de módulos MQTT, também o sistema de mensagens C2D.</span><span class="sxs-lookup"><span data-stu-id="b64b7-116">Provides two Gateway modules that expose IoTHub-style MQTT and HTTPS endpoints for telemetry upload, and in the case of MQTT module also C2D messaging.</span></span> |
| <span data-ttu-id="b64b7-117">**Raspberry Pi**</span><span class="sxs-lookup"><span data-stu-id="b64b7-117">**Raspberry Pi**</span></span> ||
| [<span data-ttu-id="b64b7-118">Introdução ao Kit de Início do Microsoft Azure IoT Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="b64b7-118">Get Started with Microsoft Azure IoT Raspberry Pi Starter Kit</span></span>](https://github.com/Azure-Samples/iot-hub-node-raspberrypi-getting-started) | <span data-ttu-id="b64b7-119">Ilustra como usar o Kit de Início do Azure IoT Raspberry Pi.</span><span class="sxs-lookup"><span data-stu-id="b64b7-119">Illustrates using the Azure IoT Raspberry Pi Starter Kit.</span></span> |
| [<span data-ttu-id="b64b7-120">Conectar o Microsoft Azure IoT Raspberry Pi 3 Starter Kit à solução de monitoramento remota</span><span class="sxs-lookup"><span data-stu-id="b64b7-120">Connect your Microsoft Azure IoT Raspberry Pi 3 Starter Kit to the remote monitoring solution</span></span>](https://azure.microsoft.com/resources/samples/iot-remote-monitoring-node-raspberrypi-getstartedkit/) | <span data-ttu-id="b64b7-121">Saiba como conectar um dispositivo Raspberry Pi 3 à solução de monitoramento remota do Azure IoT Suite.</span><span class="sxs-lookup"><span data-stu-id="b64b7-121">Learn how to connect a Raspberry Pi 3 device to the Azure IoT Suite remote monitoring solution.</span></span> |
