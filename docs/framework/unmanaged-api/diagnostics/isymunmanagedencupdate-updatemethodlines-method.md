---
description: 'Дополнительные сведения о методе: ISymUnmanagedENCUpdate:: Упдатемесодлинес'
title: Метод ISymUnmanagedENCUpdate::UpdateMethodLines
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.UpdateMethodLines
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::UpdateMethodLines
helpviewer_keywords:
- UpdateMethodLines method [.NET Framework debugging]
- ISymUnmanagedENCUpdate::UpdateMethodLines method [.NET Framework debugging]
ms.assetid: 275ef87b-0b53-49f9-af6b-58506335dc06
topic_type:
- apiref
ms.openlocfilehash: 6174f3aa980ccf2cdc07720e3aa90b7bb74a77af
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710066"
---
# <a name="isymunmanagedencupdateupdatemethodlines-method"></a><span data-ttu-id="d9863-103">Метод ISymUnmanagedENCUpdate::UpdateMethodLines</span><span class="sxs-lookup"><span data-stu-id="d9863-103">ISymUnmanagedENCUpdate::UpdateMethodLines Method</span></span>

<span data-ttu-id="d9863-104">Позволяет обновлять сведения о строке для метода, который не был перекомпилирован, но строки были перемещены независимо друг от друга.</span><span class="sxs-lookup"><span data-stu-id="d9863-104">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span></span> <span data-ttu-id="d9863-105">Допускается использование разности для каждой инструкции.</span><span class="sxs-lookup"><span data-stu-id="d9863-105">A delta for each statement is allowed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9863-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d9863-106">Syntax</span></span>  
  
```cpp  
HRESULT UpdateMethodLines(  
    [in]  mdMethodDef  mdMethodToken,  
    [in, size_is(cDeltas)] INT32*  pDeltas,  
    [in]  ULONG        cDeltas);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9863-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="d9863-107">Parameters</span></span>  

 `mdMethodToken`  
 <span data-ttu-id="d9863-108">окне Метаданные токена метода.</span><span class="sxs-lookup"><span data-stu-id="d9863-108">[in] The metadata of the method token.</span></span>  
  
 `pDeltas`  
 <span data-ttu-id="d9863-109">окне Массив `INT32` значений, указывающий разность для каждой точки следования в методе.</span><span class="sxs-lookup"><span data-stu-id="d9863-109">[in] An array of `INT32` values that indicates deltas for each sequence point in the method.</span></span>  
  
 `cDeltas`  
 <span data-ttu-id="d9863-110">окне Значение типа, `ULONG` содержащее размер `pDeltas` параметра.</span><span class="sxs-lookup"><span data-stu-id="d9863-110">[in] A `ULONG` containing the size of the `pDeltas` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d9863-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="d9863-111">Return Value</span></span>  

 <span data-ttu-id="d9863-112">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="d9863-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9863-113">Требования</span><span class="sxs-lookup"><span data-stu-id="d9863-113">Requirements</span></span>  

 <span data-ttu-id="d9863-114">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="d9863-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9863-115">См. также</span><span class="sxs-lookup"><span data-stu-id="d9863-115">See also</span></span>

- [<span data-ttu-id="d9863-116">Интерфейс ISymUnmanagedENCUpdate</span><span class="sxs-lookup"><span data-stu-id="d9863-116">ISymUnmanagedENCUpdate Interface</span></span>](isymunmanagedencupdate-interface.md)
