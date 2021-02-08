---
description: 'Дополнительные сведения о методе: IInstallReferenceItem:: IsReference'
title: Метод IInstallReferenceItem::GetReference
ms.date: 03/30/2017
api_name:
- IInstallReferenceItem.GetReference
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IInstallReferenceItem::GetReference
helpviewer_keywords:
- IInstallReferenceItem::GetReference method [.NET Framework fusion]
- GetReference method [.NET Framework fusion]
ms.assetid: 8960332f-c98a-405a-ba92-7003de0c1187
topic_type:
- apiref
ms.openlocfilehash: 88f5ca21b6f3494031e1cd232f71253e39d9e648
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800123"
---
# <a name="iinstallreferenceitemgetreference-method"></a><span data-ttu-id="5710b-103">Метод IInstallReferenceItem::GetReference</span><span class="sxs-lookup"><span data-stu-id="5710b-103">IInstallReferenceItem::GetReference Method</span></span>

<span data-ttu-id="5710b-104">Возвращает указатель на структуру [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) , представленную этим объектом [IInstallReferenceItem](iinstallreferenceitem-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="5710b-104">Gets a pointer to the [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) structure represented by this [IInstallReferenceItem](iinstallreferenceitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5710b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5710b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetReference (  
    [out] LPFUSION_INSTALL_REFERENCE *ppRefData,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5710b-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="5710b-106">Parameters</span></span>  

 `ppRefData`  
 <span data-ttu-id="5710b-107">заполняет Возвращаемый `FUSION_INSTALL_REFERENCE` указатель.</span><span class="sxs-lookup"><span data-stu-id="5710b-107">[out] The returned `FUSION_INSTALL_REFERENCE` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="5710b-108">окне Зарезервировано для будущего расширения.</span><span class="sxs-lookup"><span data-stu-id="5710b-108">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="5710b-109">`dwFlags` значение должно быть равно 0 (нулю).</span><span class="sxs-lookup"><span data-stu-id="5710b-109">`dwFlags` must be 0 (zero).</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="5710b-110">окне Зарезервировано для будущего расширения.</span><span class="sxs-lookup"><span data-stu-id="5710b-110">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="5710b-111">`pvReserved` должен быть пустой ссылкой.</span><span class="sxs-lookup"><span data-stu-id="5710b-111">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5710b-112">Требования</span><span class="sxs-lookup"><span data-stu-id="5710b-112">Requirements</span></span>  

 <span data-ttu-id="5710b-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5710b-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5710b-114">**Заголовок:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="5710b-114">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="5710b-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5710b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5710b-116">См. также</span><span class="sxs-lookup"><span data-stu-id="5710b-116">See also</span></span>

- [<span data-ttu-id="5710b-117">Интерфейс IInstallReferenceItem</span><span class="sxs-lookup"><span data-stu-id="5710b-117">IInstallReferenceItem Interface</span></span>](iinstallreferenceitem-interface.md)
- [<span data-ttu-id="5710b-118">Структура FUSION_INSTALL_REFERENCE</span><span class="sxs-lookup"><span data-stu-id="5710b-118">FUSION_INSTALL_REFERENCE Structure</span></span>](fusion-install-reference-structure.md)
