---
description: 'Дополнительные сведения о методе: ICorPublishProcessEnum:: Next'
title: Метод ICorPublishProcessEnum::Next
ms.date: 03/30/2017
api_name:
- ICorPublishProcessEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcessEnum::Next
helpviewer_keywords:
- ICorPublishProcessEnum::Next method [.NET Framework debugging]
- Next method, ICorPublishProcessEnum interface [.NET Framework debugging]
ms.assetid: 6c399f37-1e38-4ca1-b70d-8ae41f7228b7
topic_type:
- apiref
ms.openlocfilehash: 14b4f815aff986b23a22ed3d5736c37128d3d7e3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790481"
---
# <a name="icorpublishprocessenumnext-method"></a><span data-ttu-id="a359c-103">Метод ICorPublishProcessEnum::Next</span><span class="sxs-lookup"><span data-stu-id="a359c-103">ICorPublishProcessEnum::Next Method</span></span>

<span data-ttu-id="a359c-104">Возвращает указанное количество процессов из коллекции, начиная с текущего положения курсора.</span><span class="sxs-lookup"><span data-stu-id="a359c-104">Gets the specified number of processes from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a359c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a359c-105">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorPublishProcess **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a359c-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="a359c-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="a359c-107">окне Число процессов для извлечения.</span><span class="sxs-lookup"><span data-stu-id="a359c-107">[in] The number of processes to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="a359c-108">заполняет Указатель на массив полученных объектов [ICorPublishProcess](icorpublishprocess-interface.md) , каждый из которых представляет процесс.</span><span class="sxs-lookup"><span data-stu-id="a359c-108">[out] A pointer to the array of retrieved [ICorPublishProcess](icorpublishprocess-interface.md) objects, each of which represents a process.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="a359c-109">заполняет Указатель на число фактически возвращенных процессов.</span><span class="sxs-lookup"><span data-stu-id="a359c-109">[out] Pointer to the number of processes actually returned.</span></span> <span data-ttu-id="a359c-110">Это значение может быть равно NULL `celt` , если равно единице.</span><span class="sxs-lookup"><span data-stu-id="a359c-110">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a359c-111">Требования</span><span class="sxs-lookup"><span data-stu-id="a359c-111">Requirements</span></span>  

 <span data-ttu-id="a359c-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a359c-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a359c-113">**Заголовок:** Корпуб. idl, Корпуб. h</span><span class="sxs-lookup"><span data-stu-id="a359c-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="a359c-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a359c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a359c-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a359c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a359c-116">См. также</span><span class="sxs-lookup"><span data-stu-id="a359c-116">See also</span></span>

- [<span data-ttu-id="a359c-117">Интерфейс ICorPublishProcessEnum</span><span class="sxs-lookup"><span data-stu-id="a359c-117">ICorPublishProcessEnum Interface</span></span>](icorpublishprocessenum-interface.md)
