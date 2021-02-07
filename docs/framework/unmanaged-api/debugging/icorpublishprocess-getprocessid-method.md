---
description: 'Дополнительные сведения о методе: ICorPublishProcess:: GetProcessID'
title: Метод ICorPublishProcess::GetProcessID
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.GetProcessID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::GetProcessID
helpviewer_keywords:
- ICorPublishProcess::GetProcessID method [.NET Framework debugging]
- GetProcessID method [.NET Framework debugging]
ms.assetid: f31185e0-f01d-463a-b392-42163e39bfe9
topic_type:
- apiref
ms.openlocfilehash: f959a49330e0ef4ade2a878acfd287657b5086ec
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728825"
---
# <a name="icorpublishprocessgetprocessid-method"></a><span data-ttu-id="7c878-103">Метод ICorPublishProcess::GetProcessID</span><span class="sxs-lookup"><span data-stu-id="7c878-103">ICorPublishProcess::GetProcessID Method</span></span>

<span data-ttu-id="7c878-104">Возвращает идентификатор операционной системы для этого процесса.</span><span class="sxs-lookup"><span data-stu-id="7c878-104">Gets the operating system identifier for this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c878-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7c878-105">Syntax</span></span>  
  
```cpp  
HRESULT GetProcessID (  
    [out] unsigned   *pid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c878-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="7c878-106">Parameters</span></span>  

 `pid`  
 <span data-ttu-id="7c878-107">заполняет Указатель на идентификатор процесса, представленного этим объектом [ICorPublishProcess](icorpublishprocess-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="7c878-107">[out] A pointer to the identifier of the process represented by this [ICorPublishProcess](icorpublishprocess-interface.md) object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c878-108">Требования</span><span class="sxs-lookup"><span data-stu-id="7c878-108">Requirements</span></span>  

 <span data-ttu-id="7c878-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c878-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c878-110">**Заголовок:** Корпуб. idl, Корпуб. h</span><span class="sxs-lookup"><span data-stu-id="7c878-110">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="7c878-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7c878-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7c878-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c878-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c878-113">См. также</span><span class="sxs-lookup"><span data-stu-id="7c878-113">See also</span></span>

- [<span data-ttu-id="7c878-114">Интерфейс ICorPublishProcess</span><span class="sxs-lookup"><span data-stu-id="7c878-114">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)
