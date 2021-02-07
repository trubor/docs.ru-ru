---
description: 'См. Дополнительные сведения о методе IAssemblyName:: Equals'
title: Метод IAssemblyName::IsEqual
ms.date: 03/30/2017
api_name:
- IAssemblyName.IsEqual
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::IsEqual
helpviewer_keywords:
- IsEqual method [.NET Framework fusion]
- IAssemblyName::IsEqual method [.NET Framework fusion]
ms.assetid: 6dfc220f-d0d4-45b3-bfce-5829f817766f
topic_type:
- apiref
ms.openlocfilehash: f1bb0e26a217354e904ff79b397771d727a7a661
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760695"
---
# <a name="iassemblynameisequal-method"></a><span data-ttu-id="bcf5c-103">Метод IAssemblyName::IsEqual</span><span class="sxs-lookup"><span data-stu-id="bcf5c-103">IAssemblyName::IsEqual Method</span></span>

<span data-ttu-id="bcf5c-104">Определяет, равен ли указанный объект [IAssemblyName](iassemblyname-interface.md) этому объекту `IAssemblyName` на основе указанных флагов сравнения.</span><span class="sxs-lookup"><span data-stu-id="bcf5c-104">Determines whether a specified [IAssemblyName](iassemblyname-interface.md) object is equal to this `IAssemblyName`, based on the specified comparison flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcf5c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="bcf5c-105">Syntax</span></span>  
  
```cpp  
HRESULT IsEqual (  
    [in] IAssemblyName  *pName,  
    [in] DWORD          dwCmpFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bcf5c-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="bcf5c-106">Parameters</span></span>  

 `pName`  
 <span data-ttu-id="bcf5c-107">окне `IAssemblyName` Объект, с которым необходимо выполнить сравнение `IAssemblyName` .</span><span class="sxs-lookup"><span data-stu-id="bcf5c-107">[in] The `IAssemblyName` object to which to compare this `IAssemblyName`.</span></span>  
  
 `dwCmpFlags`  
 <span data-ttu-id="bcf5c-108">окне Побитовое сочетание значений [ASM_CMP_FLAGS](asm-cmp-flags-enumeration.md) , влияющих на сравнение.</span><span class="sxs-lookup"><span data-stu-id="bcf5c-108">[in] A bitwise combination of [ASM_CMP_FLAGS](asm-cmp-flags-enumeration.md) values that influence the comparison.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bcf5c-109">Требования</span><span class="sxs-lookup"><span data-stu-id="bcf5c-109">Requirements</span></span>  

 <span data-ttu-id="bcf5c-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bcf5c-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bcf5c-111">**Заголовок:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="bcf5c-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="bcf5c-112">**Версии .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bcf5c-112">**NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcf5c-113">См. также</span><span class="sxs-lookup"><span data-stu-id="bcf5c-113">See also</span></span>

- [<span data-ttu-id="bcf5c-114">Интерфейс IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="bcf5c-114">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="bcf5c-115">Перечисления Fusion</span><span class="sxs-lookup"><span data-stu-id="bcf5c-115">Fusion Enumerations</span></span>](fusion-enumerations.md)
