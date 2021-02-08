---
description: Дополнительные сведения см. в статье ресурсы операционной системы, необходимые для WCF.
title: Ресурсы операционной системы, необходимые WCF
ms.date: 03/30/2017
ms.assetid: cdd9a331-53fe-4e0d-bdfe-782264aec5c9
ms.openlocfilehash: 717ab2074c0dcf840919c2bd8afa2641e106ac11
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779222"
---
# <a name="operating-system-resources-required-by-wcf"></a><span data-ttu-id="c132f-103">Ресурсы операционной системы, необходимые WCF</span><span class="sxs-lookup"><span data-stu-id="c132f-103">Operating System Resources Required by WCF</span></span>

<span data-ttu-id="c132f-104">Windows Communication Foundation (WCF) зависит от нескольких ресурсов, предоставляемых операционной системой для работы.</span><span class="sxs-lookup"><span data-stu-id="c132f-104">Windows Communication Foundation (WCF) depends on several resources that are provided by the operating system to function.</span></span> <span data-ttu-id="c132f-105">В следующей таблице перечислены эти ресурсы.</span><span class="sxs-lookup"><span data-stu-id="c132f-105">The following table lists those resources:</span></span>

|<span data-ttu-id="c132f-106">Ресурс</span><span class="sxs-lookup"><span data-stu-id="c132f-106">Resource</span></span>|<span data-ttu-id="c132f-107">Описание</span><span class="sxs-lookup"><span data-stu-id="c132f-107">Description</span></span>|
|--------------|-----------------|
|<span data-ttu-id="c132f-108">Координатор распределенных транзакций (Майкрософт)</span><span class="sxs-lookup"><span data-stu-id="c132f-108">Microsoft Distributed Transaction Coordinator (MSDTC)</span></span>|<span data-ttu-id="c132f-109">Требуется для поддержки транзакций OleTx.</span><span class="sxs-lookup"><span data-stu-id="c132f-109">Required to support OleTx transactions.</span></span>|
|<span data-ttu-id="c132f-110">службы IIS</span><span class="sxs-lookup"><span data-stu-id="c132f-110">Internet Information Services (IIS)</span></span>|<span data-ttu-id="c132f-111">Требуется, если необходимо использовать службы IIS для размещения приложения.</span><span class="sxs-lookup"><span data-stu-id="c132f-111">Required if you want to use IIS to host your application.</span></span>|
|<span data-ttu-id="c132f-112">Служба активации Windows (WAS)</span><span class="sxs-lookup"><span data-stu-id="c132f-112">Windows Process Activation Service (WAS)</span></span>|<span data-ttu-id="c132f-113">Требуется, если необходимо использовать WAS для размещения приложения.</span><span class="sxs-lookup"><span data-stu-id="c132f-113">Required if you want to use WAS to host your application.</span></span>|
