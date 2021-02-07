---
description: 'Дополнительные сведения о методе: IAssemblyEnum:: Жетнекстассембли'
title: Метод IAssemblyEnum::GetNextAssembly
ms.date: 03/30/2017
api_name:
- IAssemblyEnum.GetNextAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyEnum::GetNextAssembly
helpviewer_keywords:
- GetNextAssembly method [.NET Framework fusion]
- IAssemblyEnum::GetNextAssembly method [.NET Framework fusion]
ms.assetid: 5d7a4ca2-5f46-4ef1-a9a2-257884e9dc11
topic_type:
- apiref
ms.openlocfilehash: 52b264b1d8efad54168a6bf69fd0c715cbfa7e2a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760824"
---
# <a name="iassemblyenumgetnextassembly-method"></a><span data-ttu-id="07c92-103">Метод IAssemblyEnum::GetNextAssembly</span><span class="sxs-lookup"><span data-stu-id="07c92-103">IAssemblyEnum::GetNextAssembly Method</span></span>

<span data-ttu-id="07c92-104">Возвращает указатель на следующее значение [IAssemblyName](iassemblyname-interface.md) , содержащееся в этом объекте [IAssemblyEnum](iassemblyenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="07c92-104">Gets a pointer to the next [IAssemblyName](iassemblyname-interface.md) contained in this [IAssemblyEnum](iassemblyenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07c92-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="07c92-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNextAssembly (  
    [in]  LPVOID          pvReserved,  
    [out] IAssemblyName   **ppName,  
    [in]  DWORD           dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="07c92-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="07c92-106">Parameters</span></span>  

 `pvReserved`  
 <span data-ttu-id="07c92-107">окне Зарезервировано для будущего расширения.</span><span class="sxs-lookup"><span data-stu-id="07c92-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="07c92-108">`pvReserved` должен быть пустой ссылкой.</span><span class="sxs-lookup"><span data-stu-id="07c92-108">`pvReserved` must be a null reference.</span></span>  
  
 `ppName`  
 <span data-ttu-id="07c92-109">заполняет Возвращаемый `IAssemblyName` указатель.</span><span class="sxs-lookup"><span data-stu-id="07c92-109">[out] The returned `IAssemblyName` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="07c92-110">окне Зарезервировано для будущего расширения.</span><span class="sxs-lookup"><span data-stu-id="07c92-110">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="07c92-111">`dwFlags` значение должно быть равно 0 (нулю).</span><span class="sxs-lookup"><span data-stu-id="07c92-111">`dwFlags` must be 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07c92-112">Требования</span><span class="sxs-lookup"><span data-stu-id="07c92-112">Requirements</span></span>  

 <span data-ttu-id="07c92-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07c92-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07c92-114">**Заголовок:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="07c92-114">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="07c92-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07c92-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07c92-116">См. также</span><span class="sxs-lookup"><span data-stu-id="07c92-116">See also</span></span>

- [<span data-ttu-id="07c92-117">Интерфейс IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="07c92-117">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="07c92-118">Интерфейс IAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="07c92-118">IAssemblyEnum Interface</span></span>](iassemblyenum-interface.md)
