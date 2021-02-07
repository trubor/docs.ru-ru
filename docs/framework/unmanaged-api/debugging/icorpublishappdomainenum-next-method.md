---
description: 'Дополнительные сведения о методе: ICorPublishAppDomainEnum:: Next'
title: Метод ICorPublishAppDomainEnum::Next
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomainEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomainEnum::Next
helpviewer_keywords:
- Next method, ICorPublishAppDomainEnum interface [.NET Framework debugging]
- ICorPublishAppDomainEnum::Next method [.NET Framework debugging]
ms.assetid: ad37cd10-0339-4d08-9b0e-4b3428bb4dc3
topic_type:
- apiref
ms.openlocfilehash: 8e8255aa2326c6f0678132f5735d6cdf504dcbd0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721727"
---
# <a name="icorpublishappdomainenumnext-method"></a><span data-ttu-id="524b5-103">Метод ICorPublishAppDomainEnum::Next</span><span class="sxs-lookup"><span data-stu-id="524b5-103">ICorPublishAppDomainEnum::Next Method</span></span>

<span data-ttu-id="524b5-104">Возвращает указанное количество доменов приложений, которые в данный момент существуют в процессе, начиная с текущей позиции.</span><span class="sxs-lookup"><span data-stu-id="524b5-104">Gets the specified number of application domains that currently exist in the process, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="524b5-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="524b5-105">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]
        ICorPublishAppDomain **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="524b5-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="524b5-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="524b5-107">окне Число извлекаемых элементов.</span><span class="sxs-lookup"><span data-stu-id="524b5-107">[in] The number of elements to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="524b5-108">заполняет Указатель на массив полученных объектов [ICorPublishAppDomain](icorpublishappdomain-interface.md) , каждый из которых представляет домен приложения.</span><span class="sxs-lookup"><span data-stu-id="524b5-108">[out] A pointer to the array of retrieved [ICorPublishAppDomain](icorpublishappdomain-interface.md) objects, each of which represents an application domain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="524b5-109">заполняет Указатель на число фактически возвращенных доменов приложений.</span><span class="sxs-lookup"><span data-stu-id="524b5-109">[out] Pointer to the number of application domains actually returned.</span></span> <span data-ttu-id="524b5-110">Это значение может быть равно NULL `celt` , если равно единице.</span><span class="sxs-lookup"><span data-stu-id="524b5-110">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="524b5-111">Требования</span><span class="sxs-lookup"><span data-stu-id="524b5-111">Requirements</span></span>  

 <span data-ttu-id="524b5-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="524b5-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="524b5-113">**Заголовок:** Корпуб. idl, Корпуб. h</span><span class="sxs-lookup"><span data-stu-id="524b5-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="524b5-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="524b5-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="524b5-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="524b5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="524b5-116">См. также</span><span class="sxs-lookup"><span data-stu-id="524b5-116">See also</span></span>

- [<span data-ttu-id="524b5-117">Интерфейс ICorPublishAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="524b5-117">ICorPublishAppDomainEnum Interface</span></span>](icorpublishappdomainenum-interface.md)
