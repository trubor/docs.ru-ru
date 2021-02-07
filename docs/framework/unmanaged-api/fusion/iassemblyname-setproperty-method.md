---
description: 'Дополнительные сведения о методе IAssemblyName:: SetProperty.'
title: Метод IAssemblyName::SetProperty
ms.date: 03/30/2017
api_name:
- IAssemblyName.SetProperty
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::SetProperty
helpviewer_keywords:
- IAssemblyName::SetProperty method [.NET Framework fusion]
- SetProperty method [.NET Framework fusion]
ms.assetid: 496c3add-f60b-4073-943f-d1bcf33330cb
topic_type:
- apiref
ms.openlocfilehash: cab132c2cd8a0744a2a946a1d8b21f49012c6eac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760694"
---
# <a name="iassemblynamesetproperty-method"></a><span data-ttu-id="698ee-103">Метод IAssemblyName::SetProperty</span><span class="sxs-lookup"><span data-stu-id="698ee-103">IAssemblyName::SetProperty Method</span></span>

<span data-ttu-id="698ee-104">Задает значение свойства, на которое ссылается указанный идентификатор свойства.</span><span class="sxs-lookup"><span data-stu-id="698ee-104">Sets the value of the property referenced by the specified property identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="698ee-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="698ee-105">Syntax</span></span>  
  
```cpp  
HRESULT SetProperty (  
    [in] DWORD  PropertyId,  
    [in] LPVOID pvProperty,  
    [in] DWORD  cbProperty  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="698ee-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="698ee-106">Parameters</span></span>  

 `PropertyId`  
 <span data-ttu-id="698ee-107">окне Уникальный идентификатор свойства, значение которого будет задано.</span><span class="sxs-lookup"><span data-stu-id="698ee-107">[in] The unique identifier of the property whose value will be set.</span></span>  
  
 `pvProperty`  
 <span data-ttu-id="698ee-108">окне Значение, для которого задается свойство, на которое ссылается `PropertyId` .</span><span class="sxs-lookup"><span data-stu-id="698ee-108">[in] The value to which to set the property referenced by `PropertyId`.</span></span>  
  
 `cbProperty`  
 <span data-ttu-id="698ee-109">окне Размер (в байтах) `pvProperty` .</span><span class="sxs-lookup"><span data-stu-id="698ee-109">[in] The size, in bytes, of `pvProperty`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="698ee-110">Требования</span><span class="sxs-lookup"><span data-stu-id="698ee-110">Requirements</span></span>  

 <span data-ttu-id="698ee-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="698ee-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="698ee-112">**Заголовок:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="698ee-112">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="698ee-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="698ee-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="698ee-114">См. также</span><span class="sxs-lookup"><span data-stu-id="698ee-114">See also</span></span>

- [<span data-ttu-id="698ee-115">Интерфейс IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="698ee-115">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
