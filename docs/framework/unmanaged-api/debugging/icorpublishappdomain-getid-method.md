---
description: 'Дополнительные сведения о методе: ICorPublishAppDomain:: GetID'
title: Метод ICorPublishAppDomain::GetID
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomain.GetID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomain::GetID
helpviewer_keywords:
- GetID method, ICorPublishAppDomain interface [.NET Framework debugging]
- ICorPublishAppDomain::GetID method [.NET Framework debugging]
ms.assetid: 229437e3-1465-4bd8-8846-9804b2488133
topic_type:
- apiref
ms.openlocfilehash: b3de19c053b5fcce2af5e0036ee6174b01700aac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721844"
---
# <a name="icorpublishappdomaingetid-method"></a><span data-ttu-id="31ce1-103">Метод ICorPublishAppDomain::GetID</span><span class="sxs-lookup"><span data-stu-id="31ce1-103">ICorPublishAppDomain::GetID Method</span></span>

<span data-ttu-id="31ce1-104">Возвращает уникальный идентификатор для этого [ICorPublishAppDomain](icorpublishappdomain-interface.md).</span><span class="sxs-lookup"><span data-stu-id="31ce1-104">Gets the unique identifier for this [ICorPublishAppDomain](icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31ce1-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="31ce1-105">Syntax</span></span>  
  
```cpp  
HRESULT GetID (  
    [out] ULONG32   *puId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31ce1-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="31ce1-106">Parameters</span></span>  

 `puId`  
 <span data-ttu-id="31ce1-107">заполняет Указатель на идентификатор домена приложения.</span><span class="sxs-lookup"><span data-stu-id="31ce1-107">[out] A pointer to the identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31ce1-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="31ce1-108">Remarks</span></span>  

 <span data-ttu-id="31ce1-109">Идентификатор уникален только в области содержащего его процесса.</span><span class="sxs-lookup"><span data-stu-id="31ce1-109">The identifier is unique only in the scope of the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31ce1-110">Требования</span><span class="sxs-lookup"><span data-stu-id="31ce1-110">Requirements</span></span>  

 <span data-ttu-id="31ce1-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31ce1-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31ce1-112">**Заголовок:** Корпуб. idl, Корпуб. h</span><span class="sxs-lookup"><span data-stu-id="31ce1-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="31ce1-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="31ce1-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="31ce1-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31ce1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31ce1-115">См. также</span><span class="sxs-lookup"><span data-stu-id="31ce1-115">See also</span></span>

- [<span data-ttu-id="31ce1-116">Интерфейс ICorPublishAppDomain</span><span class="sxs-lookup"><span data-stu-id="31ce1-116">ICorPublishAppDomain Interface</span></span>](icorpublishappdomain-interface.md)
