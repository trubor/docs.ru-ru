---
description: 'Подробнее: гибкость шифрования в безопасности WCF'
title: Гибкость шифрования в безопасности WCF
ms.date: 03/30/2017
ms.assetid: c2c549e5-ac19-40c5-b686-8f67f52b6dbf
ms.openlocfilehash: ab46034b16a846f7399220480fc928655d931be0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778351"
---
# <a name="cryptographic-agility-in-wcf-security"></a><span data-ttu-id="95a1d-103">Гибкость шифрования в безопасности WCF</span><span class="sxs-lookup"><span data-stu-id="95a1d-103">Cryptographic agility in WCF security</span></span>

<span data-ttu-id="95a1d-104">В этом примере показано, как указать в стандартном или пользовательском алгоритме, чтобы обеспечить динамическую реализацию в клиенте Windows Communication Foundation (WCF) и службе.</span><span class="sxs-lookup"><span data-stu-id="95a1d-104">This sample shows how to specify in a standard/custom algorithm to provide a cryptographic agile implementation in a Windows Communication Foundation (WCF) client and service.</span></span> <span data-ttu-id="95a1d-105">Образец состоит из следующих проектов.</span><span class="sxs-lookup"><span data-stu-id="95a1d-105">The sample is composed of the following projects:</span></span>

<span data-ttu-id="95a1d-106">**Служба**</span><span class="sxs-lookup"><span data-stu-id="95a1d-106">**Service**</span></span>

<span data-ttu-id="95a1d-107">Это автономная служба WCF, которая реализует `ICalculator` интерфейс и защищает конечную точку с помощью <xref:System.ServiceModel.WSHttpBinding> с защищенным сеансом и отключенным надежным сеансом.</span><span class="sxs-lookup"><span data-stu-id="95a1d-107">This is a self-hosted WCF service that implements the `ICalculator` interface and secures the endpoint using the <xref:System.ServiceModel.WSHttpBinding> with secure session and reliable session disabled.</span></span> <span data-ttu-id="95a1d-108">Служба определяет пользовательский класс `SecurityAlgorithmSuite`, который задает алгоритмы шифрования, используемые для защиты сообщений.</span><span class="sxs-lookup"><span data-stu-id="95a1d-108">The service defines a custom `SecurityAlgorithmSuite` class to specify the cryptographic algorithms to be used for message security.</span></span>

<span data-ttu-id="95a1d-109">**Клиент**</span><span class="sxs-lookup"><span data-stu-id="95a1d-109">**Client**</span></span>

<span data-ttu-id="95a1d-110">Это клиент WCF, который обращается к службе после успешной проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="95a1d-110">This is a WCF client that accesses the service after successful authentication.</span></span> <span data-ttu-id="95a1d-111">Он вызывает операции, предоставляемые интерфейсом `ICalculator` и реализуемые службой.</span><span class="sxs-lookup"><span data-stu-id="95a1d-111">It invokes the operations exposed by the `ICalculator` interface and implemented by the service.</span></span> <span data-ttu-id="95a1d-112">Клиент также определяет тот же пользовательский класс `SecurityAlgorithmSuite`, который задает алгоритмы шифрования, используемые для защиты сообщений.</span><span class="sxs-lookup"><span data-stu-id="95a1d-112">The client also defines the same custom `SecurityAlgorithmSuite` class to specify the cryptographic algorithms to be used for message security.</span></span>

## <a name="to-use-this-sample"></a><span data-ttu-id="95a1d-113">Использование этого образца</span><span class="sxs-lookup"><span data-stu-id="95a1d-113">To use this sample</span></span>

1. <span data-ttu-id="95a1d-114">Откройте решение Криптоагилити. sln в Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="95a1d-114">Open the CryptoAgility.sln solution in Visual Studio 2012.</span></span>

2. <span data-ttu-id="95a1d-115">Чтобы построить решение, нажмите CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="95a1d-115">Press CTRL+SHIFT+B to build the solution.</span></span>

3. <span data-ttu-id="95a1d-116">Откройте проводник и перейдите в каталог \Вкф\басик\секурити\криптоагилити\сервице\бин и запустите файл service.exe с правами администратора, щелкнув правой кнопкой мыши service.exe и выбрав **Запуск от имени администратора**.</span><span class="sxs-lookup"><span data-stu-id="95a1d-116">Open File Explorer and navigate to the \WCF\Basic\Security\CryptoAgility\Service\bin directory and run the service.exe file with administrator privileges by right-clicking service.exe and selecting **Run as administrator**.</span></span>

4. <span data-ttu-id="95a1d-117">Перейдите в каталог \WCF\Basic\Security\CryptoAgility\Client\bin и запустите файл client.exe обычным образом.</span><span class="sxs-lookup"><span data-stu-id="95a1d-117">Navigate to \WCF\Basic\Security\CryptoAgility\Client\bin directory and run the client.exe file normally.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="95a1d-118">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="95a1d-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="95a1d-119">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="95a1d-119">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="95a1d-120">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="95a1d-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="95a1d-121">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="95a1d-121">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Security\CryptoAgility`

## <a name="see-also"></a><span data-ttu-id="95a1d-122">См. также</span><span class="sxs-lookup"><span data-stu-id="95a1d-122">See also</span></span>

- [<span data-ttu-id="95a1d-123">Безопасность Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="95a1d-123">Windows Communication Foundation Security</span></span>](../feature-details/security.md)
