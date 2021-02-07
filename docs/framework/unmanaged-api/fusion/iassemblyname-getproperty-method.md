---
description: 'Дополнительные сведения о методе IAssemblyName:: Property'
title: Метод IAssemblyName::GetProperty
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetProperty
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetProperty
helpviewer_keywords:
- IAssemblyName::GetProperty method [.NET Framework fusion]
- GetProperty method [.NET Framework fusion]
ms.assetid: e59fda62-77d5-4e37-89cb-ce7ae4627975
topic_type:
- apiref
ms.openlocfilehash: 66528bb54e1cb4adbba8fa87088065bc40c2ee15
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760737"
---
# <a name="iassemblynamegetproperty-method"></a><span data-ttu-id="82027-103">Метод IAssemblyName::GetProperty</span><span class="sxs-lookup"><span data-stu-id="82027-103">IAssemblyName::GetProperty Method</span></span>

<span data-ttu-id="82027-104">Возвращает указатель на свойство, на которое ссылается указанный идентификатор свойства.</span><span class="sxs-lookup"><span data-stu-id="82027-104">Gets a pointer to the property referenced by the specified property identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82027-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="82027-105">Syntax</span></span>  
  
```cpp  
HRESULT GetProperty (  
    [in]      DWORD    PropertyId,  
    [out]     LPVOID   pvProperty,  
    [in, out] LPDWORD  pcbProperty  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="82027-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="82027-106">Parameters</span></span>  

 `PropertyId`  
 <span data-ttu-id="82027-107">окне Уникальный идентификатор запрошенного свойства.</span><span class="sxs-lookup"><span data-stu-id="82027-107">[in] The unique identifier for the requested property.</span></span>  
  
 `pvProperty`  
 <span data-ttu-id="82027-108">заполняет Возвращаемые данные свойства.</span><span class="sxs-lookup"><span data-stu-id="82027-108">[out] The returned property data.</span></span>  
  
 `pcbProperty`  
 <span data-ttu-id="82027-109">[вход, выход] Размер (в байтах) `pvProperty` .</span><span class="sxs-lookup"><span data-stu-id="82027-109">[in, out] The size, in bytes, of `pvProperty`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82027-110">Требования</span><span class="sxs-lookup"><span data-stu-id="82027-110">Requirements</span></span>  

 <span data-ttu-id="82027-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82027-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82027-112">**Заголовок:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="82027-112">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="82027-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82027-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82027-114">См. также</span><span class="sxs-lookup"><span data-stu-id="82027-114">See also</span></span>

- [<span data-ttu-id="82027-115">Интерфейс IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="82027-115">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
