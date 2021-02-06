---
description: 'Дополнительные сведения: метод ICLRRuntimeInfo:: BindAsLegacyV2Runtime'
title: Метод ICLRRuntimeInfo::BindAsLegacyV2Runtime
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.BindAsLegacyV2Runtime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::BindAsLegacyV2Runtime
helpviewer_keywords:
- ICLRRuntimeInfo::BindAsLegacyV2Runtime method [.NET Framework hosting]
- BindAsLegacyV2Runtime method [.NET Framework hosting]
ms.assetid: 65fd55ac-4a24-4479-9384-a2e8013bfb2b
topic_type:
- apiref
ms.openlocfilehash: 77b340cba18ea86546e1a8f4a17933f09289b1de
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637186"
---
# <a name="iclrruntimeinfobindaslegacyv2runtime-method"></a><span data-ttu-id="c9326-103">Метод ICLRRuntimeInfo::BindAsLegacyV2Runtime</span><span class="sxs-lookup"><span data-stu-id="c9326-103">ICLRRuntimeInfo::BindAsLegacyV2Runtime Method</span></span>

<span data-ttu-id="c9326-104">Привязывает текущую среду выполнения для всех устаревших решений политики активации среды CLR версии 2.</span><span class="sxs-lookup"><span data-stu-id="c9326-104">Binds the current runtime for all legacy common language runtime (CLR) version 2 activation policy decisions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9326-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c9326-105">Syntax</span></span>  
  
```cpp  
HRESULT BindAsLegacyV2Runtime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="c9326-106">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="c9326-106">Return Value</span></span>  

 <span data-ttu-id="c9326-107">Этот метод возвращает следующие определенные значения HRESULT:</span><span class="sxs-lookup"><span data-stu-id="c9326-107">This method returns the following specific HRESULTs:</span></span>  
  
|<span data-ttu-id="c9326-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c9326-108">HRESULT</span></span>|<span data-ttu-id="c9326-109">Описание:</span><span class="sxs-lookup"><span data-stu-id="c9326-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c9326-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c9326-110">S_OK</span></span>|<span data-ttu-id="c9326-111">Либо привязка выполнена успешно, либо эта среда выполнения уже была привязана к устаревшей среде выполнения политики активации CLR версии 2.</span><span class="sxs-lookup"><span data-stu-id="c9326-111">Either binding succeeded, or this runtime was already bound as the legacy CLR version 2 activation policy runtime.</span></span>|  
|<span data-ttu-id="c9326-112">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span><span class="sxs-lookup"><span data-stu-id="c9326-112">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span></span>|<span data-ttu-id="c9326-113">Другая среда выполнения уже привязана к устаревшей политике активации CLR версии 2.</span><span class="sxs-lookup"><span data-stu-id="c9326-113">A different runtime was already bound to the legacy CLR version 2 activation policy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9326-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="c9326-114">Remarks</span></span>  

 <span data-ttu-id="c9326-115">Если текущая среда выполнения уже привязана для всех устаревших решений политики активации CLR версии 2 (например, с помощью `useLegacyV2RuntimeActivationPolicy` атрибута [ \<startup> элемента](../../configure-apps/file-schema/startup/startup-element.md) в файле конфигурации), этот метод не возвращает результат ошибки; вместо этого результат S_OK, как если бы метод успешно привязать политику активации прежних версий.</span><span class="sxs-lookup"><span data-stu-id="c9326-115">If the current runtime is already bound for all legacy CLR version 2 activation policy decisions (for example, by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> element](../../configure-apps/file-schema/startup/startup-element.md) in the configuration file), this method does not return an error result; instead, the result is S_OK, just as it would be if the method had successfully bound legacy activation policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9326-116">Требования</span><span class="sxs-lookup"><span data-stu-id="c9326-116">Requirements</span></span>  

 <span data-ttu-id="c9326-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9326-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9326-118">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="c9326-118">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="c9326-119">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c9326-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c9326-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9326-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9326-121">См. также</span><span class="sxs-lookup"><span data-stu-id="c9326-121">See also</span></span>

- [<span data-ttu-id="c9326-122">Интерфейс ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="c9326-122">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="c9326-123">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="c9326-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="c9326-124">Размещение</span><span class="sxs-lookup"><span data-stu-id="c9326-124">Hosting</span></span>](index.md)
- [<span data-ttu-id="c9326-125">\<startup> Элемент</span><span class="sxs-lookup"><span data-stu-id="c9326-125">\<startup> Element</span></span>](../../configure-apps/file-schema/startup/startup-element.md)
