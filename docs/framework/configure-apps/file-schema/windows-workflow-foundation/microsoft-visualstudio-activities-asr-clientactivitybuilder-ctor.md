---
description: 'Дополнительные сведения: Microsoft. VisualStudio. Activitys. ASR. Клиентактивитибуилдер.. разрешен'
title: Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor
ms.date: 03/30/2017
ms.topic: reference
api_name:
- Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor
api_location:
- Microsoft.VisualStudio.Activities.dll
api_type:
- Assembly
ms.assetid: 6b44b13c-7a23-4df2-8f9f-45e2b1430002
ms.openlocfilehash: 1a1b436c2b15fdf07f924aa0db2a13598422e988
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739993"
---
# <a name="microsoftvisualstudioactivitiesasrclientactivitybuilderctor"></a><span data-ttu-id="605f3-103">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor</span><span class="sxs-lookup"><span data-stu-id="605f3-103">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor</span></span>

<span data-ttu-id="605f3-104">Создает экземпляр класса [Microsoft. VisualStudio. activitys. ASR. клиентактивитибуилдер](microsoft-visualstudio-activities-asr-clientactivitybuilder.md) .</span><span class="sxs-lookup"><span data-stu-id="605f3-104">Creates an instance of the [Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](microsoft-visualstudio-activities-asr-clientactivitybuilder.md) class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="605f3-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="605f3-105">Syntax</span></span>  
  
```csharp  
public ClientActivityBuilder(OperationDescription operationDescription, string configurationName, string proxyNamespace);  
```  
  
## <a name="parameters"></a><span data-ttu-id="605f3-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="605f3-106">Parameters</span></span>  
  
## <a name="parameter-values"></a><span data-ttu-id="605f3-107">Значения параметров</span><span class="sxs-lookup"><span data-stu-id="605f3-107">Parameter Values</span></span>  

 <span data-ttu-id="605f3-108">*operationDescription*</span><span class="sxs-lookup"><span data-stu-id="605f3-108">*operationDescription*</span></span>  
  
 <span data-ttu-id="605f3-109">описывает операцию, выполняемую в создаваемом действии рабочего процесса. Содержит имя операции, тип возвращаемого значения и сведения о параметрах.</span><span class="sxs-lookup"><span data-stu-id="605f3-109">Describes the operation to be performed in the workflow activity that is to be generated, including the operation name, return type, and parameter information.</span></span> <span data-ttu-id="605f3-110">Значение этого параметра не должно быть **равно NULL**.</span><span class="sxs-lookup"><span data-stu-id="605f3-110">The value of this parameter must not be **null**.</span></span> <span data-ttu-id="605f3-111">Он должен описывать синхронную операцию, в которой используется данный контракт сообщений и принимается аргумент с одним сообщением.</span><span class="sxs-lookup"><span data-stu-id="605f3-111">It should describe a synchronous operation which uses a message contract and takes an argument with one message.</span></span> <span data-ttu-id="605f3-112">Если эти условия не выполняются, то во время выполнения результаты использования конструктора и других методов этого класса будут неопределенными.</span><span class="sxs-lookup"><span data-stu-id="605f3-112">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
 <span data-ttu-id="605f3-113">*Указав*</span><span class="sxs-lookup"><span data-stu-id="605f3-113">*configurationName*</span></span>  
  
 <span data-ttu-id="605f3-114">указывает имя конфигурации конечной точки.</span><span class="sxs-lookup"><span data-stu-id="605f3-114">Specifies the endpoint configuration name.</span></span> <span data-ttu-id="605f3-115">Значение этого параметра не должно быть **null** или пустым.</span><span class="sxs-lookup"><span data-stu-id="605f3-115">The value of this parameter must not be either **null** or empty.</span></span> <span data-ttu-id="605f3-116">Если эти условия не выполняются, то во время выполнения результаты использования конструктора и других методов этого класса будут неопределенными.</span><span class="sxs-lookup"><span data-stu-id="605f3-116">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
 <span data-ttu-id="605f3-117">*проксинамеспаце*</span><span class="sxs-lookup"><span data-stu-id="605f3-117">*proxyNamespace*</span></span>  
  
 <span data-ttu-id="605f3-118">указывает пространство имен службы для операции.</span><span class="sxs-lookup"><span data-stu-id="605f3-118">Specifies the service namespace for the operation.</span></span> <span data-ttu-id="605f3-119">Значение этого параметра не должно быть **null** или пустым.</span><span class="sxs-lookup"><span data-stu-id="605f3-119">The value of this parameter must not be either **null** or empty.</span></span> <span data-ttu-id="605f3-120">Если эти условия не выполняются, то во время выполнения результаты использования конструктора и других методов этого класса будут неопределенными.</span><span class="sxs-lookup"><span data-stu-id="605f3-120">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="605f3-121">См. также</span><span class="sxs-lookup"><span data-stu-id="605f3-121">See also</span></span>

- [<span data-ttu-id="605f3-122">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder</span><span class="sxs-lookup"><span data-stu-id="605f3-122">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder</span></span>](microsoft-visualstudio-activities-asr-clientactivitybuilder.md)
