---
description: 'Дополнительные сведения о методе: IInstallReferenceEnum:: Жетнекстинсталлреференцеитем'
title: Метод IInstallReferenceEnum::GetNextInstallReferenceItem
ms.date: 03/30/2017
api_name:
- IInstallReferenceEnum.GetNextInstallReferenceItem
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IInstallReferenceEnum::GetNextInstallReferenceItem
helpviewer_keywords:
- IInstallReferenceEnum::GetNextInstallReferenceItem method [.NET Framework fusion]
- GetNextInstallReferenceItem method [.NET Framework fusion]
ms.assetid: ce969c9d-6538-4c34-8784-148ffd99fe7a
topic_type:
- apiref
ms.openlocfilehash: d410407fe16a46b45786ff74f694aaa8931be542
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800127"
---
# <a name="iinstallreferenceenumgetnextinstallreferenceitem-method"></a><span data-ttu-id="958f6-103">Метод IInstallReferenceEnum::GetNextInstallReferenceItem</span><span class="sxs-lookup"><span data-stu-id="958f6-103">IInstallReferenceEnum::GetNextInstallReferenceItem Method</span></span>

<span data-ttu-id="958f6-104">Возвращает указатель на следующий объект [IInstallReferenceItem](iinstallreferenceitem-interface.md) , содержащийся в этом объекте [IInstallReferenceEnum](iinstallreferenceenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="958f6-104">Gets a pointer to the next [IInstallReferenceItem](iinstallreferenceitem-interface.md) object contained in this [IInstallReferenceEnum](iinstallreferenceenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="958f6-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="958f6-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNextInstallReferenceItem (  
    [out] IInstallReferenceItem **ppRefItem,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="958f6-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="958f6-106">Parameters</span></span>  

 `ppRefItem`  
 <span data-ttu-id="958f6-107">заполняет Возвращаемый `IInstallReferenceItem` указатель.</span><span class="sxs-lookup"><span data-stu-id="958f6-107">[out] The returned `IInstallReferenceItem` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="958f6-108">окне Зарезервировано для будущего расширения.</span><span class="sxs-lookup"><span data-stu-id="958f6-108">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="958f6-109">`dwFlags` значение должно быть равно 0 (нулю).</span><span class="sxs-lookup"><span data-stu-id="958f6-109">`dwFlags` must be 0 (zero).</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="958f6-110">окне Зарезервировано для будущего расширения.</span><span class="sxs-lookup"><span data-stu-id="958f6-110">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="958f6-111">`pvReserved` должен быть пустой ссылкой.</span><span class="sxs-lookup"><span data-stu-id="958f6-111">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="958f6-112">Требования</span><span class="sxs-lookup"><span data-stu-id="958f6-112">Requirements</span></span>  

 <span data-ttu-id="958f6-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="958f6-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="958f6-114">**Заголовок:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="958f6-114">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="958f6-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="958f6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="958f6-116">См. также</span><span class="sxs-lookup"><span data-stu-id="958f6-116">See also</span></span>

- [<span data-ttu-id="958f6-117">Интерфейс IInstallReferenceItem</span><span class="sxs-lookup"><span data-stu-id="958f6-117">IInstallReferenceItem Interface</span></span>](iinstallreferenceitem-interface.md)
- [<span data-ttu-id="958f6-118">Интерфейс IInstallReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="958f6-118">IInstallReferenceEnum Interface</span></span>](iinstallreferenceenum-interface.md)
