---
description: 'Дополнительные сведения о: интерфейс ICLRMetaHostPolicy'
title: Интерфейс ICLRMetaHostPolicy
ms.date: 03/30/2017
api_name:
- ICLRMetaHostPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHostPolicy
helpviewer_keywords:
- ICLRMetaHostPolicy interface [.NET Framework hosting]
ms.assetid: 1bdeccb6-0698-4c97-ad69-eae2b69e59f1
topic_type:
- apiref
ms.openlocfilehash: b14ad417617c32242f8a59844f7c1f1a8d05c78d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637421"
---
# <a name="iclrmetahostpolicy-interface"></a><span data-ttu-id="e3e1d-103">Интерфейс ICLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="e3e1d-103">ICLRMetaHostPolicy Interface</span></span>

<span data-ttu-id="e3e1d-104">Предоставляет метод [GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) , возвращающий указатель на интерфейс среды CLR на основе критериев политики, управляемой сборки, версии и файла конфигурации.</span><span class="sxs-lookup"><span data-stu-id="e3e1d-104">Provides the [GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) method, which returns a pointer to a common language runtime (CLR) interface based on a policy criteria, managed assembly, version and configuration file.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e3e1d-105">Методы</span><span class="sxs-lookup"><span data-stu-id="e3e1d-105">Methods</span></span>  
  
|<span data-ttu-id="e3e1d-106">Метод</span><span class="sxs-lookup"><span data-stu-id="e3e1d-106">Method</span></span>|<span data-ttu-id="e3e1d-107">Описание</span><span class="sxs-lookup"><span data-stu-id="e3e1d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e3e1d-108">Метод GetRequestedRuntime</span><span class="sxs-lookup"><span data-stu-id="e3e1d-108">GetRequestedRuntime Method</span></span>](iclrmetahostpolicy-getrequestedruntime-method.md)|<span data-ttu-id="e3e1d-109">Предоставляет предпочтительный интерфейс CLR на основе критериев политики, управляемой сборки, версии и файла конфигурации.</span><span class="sxs-lookup"><span data-stu-id="e3e1d-109">Provides a preferred CLR interface based on a policy criteria, managed assembly, version, and configuration file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3e1d-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="e3e1d-110">Remarks</span></span>  

 <span data-ttu-id="e3e1d-111">Ссылку на этот интерфейс можно получить, вызвав функцию [клркреатеинстанце](clrcreateinstance-function.md) , как показано в следующем коде:</span><span class="sxs-lookup"><span data-stu-id="e3e1d-111">You can get a reference to this interface by calling the [CLRCreateInstance](clrcreateinstance-function.md) function as shown in the following code:</span></span>  
  
```cpp  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHostPolicy,  
                   IID_ICLRMetaHostPolicy, (LPVOID*)&pMetaHostPolicy);  
```  
  
> [!NOTE]
> <span data-ttu-id="e3e1d-112">Этот интерфейс фактически не загружает и не активирует среду CLR, а просто возвращает предпочтительную версию среды CLR на основе установленных или загруженных версий.</span><span class="sxs-lookup"><span data-stu-id="e3e1d-112">This interface does not actually load or activate the CLR, but simply returns the preferred CLR version based on the available versions that are installed or loaded.</span></span>  
  
 <span data-ttu-id="e3e1d-113">В платформа .NET Framework 4 API размещения консолидируются политики, чтобы узлы с конкретными потребностями могли использовать базовые функции без непреднамеренной потерь.</span><span class="sxs-lookup"><span data-stu-id="e3e1d-113">The .NET Framework 4 hosting API consolidates policies so that hosts with specific needs may use basic functionality without incurring unintended penalties.</span></span> <span data-ttu-id="e3e1d-114">Например, многие из MSCorEE.dll экспортов будут привязаны к определенной среде CLR, хотя метод может не потребовать его логически.</span><span class="sxs-lookup"><span data-stu-id="e3e1d-114">For example, many of the MSCorEE.dll exports will bind to a specific CLR, although a method might not logically require it.</span></span> <span data-ttu-id="e3e1d-115">Перечисление [METAHOST_POLICY_FLAGS](metahost-policy-flags-enumeration.md) предоставляет политики привязки, общие для большинства узлов.</span><span class="sxs-lookup"><span data-stu-id="e3e1d-115">The [METAHOST_POLICY_FLAGS](metahost-policy-flags-enumeration.md) enumeration provides binding policies that are common to the majority of hosts.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3e1d-116">Требования</span><span class="sxs-lookup"><span data-stu-id="e3e1d-116">Requirements</span></span>  

 <span data-ttu-id="e3e1d-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3e1d-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3e1d-118">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="e3e1d-118">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="e3e1d-119">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e3e1d-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e3e1d-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3e1d-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3e1d-121">См. также</span><span class="sxs-lookup"><span data-stu-id="e3e1d-121">See also</span></span>

- [<span data-ttu-id="e3e1d-122">Интерфейсы размещения CLR, добавленные в версиях .NET Framework 4 и 4.5</span><span class="sxs-lookup"><span data-stu-id="e3e1d-122">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="e3e1d-123">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="e3e1d-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="e3e1d-124">Размещение</span><span class="sxs-lookup"><span data-stu-id="e3e1d-124">Hosting</span></span>](index.md)
