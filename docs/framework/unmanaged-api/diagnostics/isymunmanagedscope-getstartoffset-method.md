---
description: 'Дополнительные сведения о методе: Исимунманажедскопе:: Жетстартоффсет'
title: Метод ISymUnmanagedScope::GetStartOffset
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetStartOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetStartOffset
helpviewer_keywords:
- GetStartOffset method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetStartOffset method [.NET Framework debugging]
ms.assetid: da6bbc75-94d1-4354-9722-0d455b4428fb
topic_type:
- apiref
ms.openlocfilehash: c95fbc5229512f08052ffc00f0092f64983ea3f6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763323"
---
# <a name="isymunmanagedscopegetstartoffset-method"></a><span data-ttu-id="4dcd6-103">Метод ISymUnmanagedScope::GetStartOffset</span><span class="sxs-lookup"><span data-stu-id="4dcd6-103">ISymUnmanagedScope::GetStartOffset Method</span></span>

<span data-ttu-id="4dcd6-104">Возвращает начальное смещение для этой области.</span><span class="sxs-lookup"><span data-stu-id="4dcd6-104">Gets the start offset for this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4dcd6-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4dcd6-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4dcd6-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="4dcd6-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="4dcd6-107">заполняет Указатель на объект `ULONG32` , содержащий начальное смещение.</span><span class="sxs-lookup"><span data-stu-id="4dcd6-107">[out] A pointer to a `ULONG32` that contains the starting offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4dcd6-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="4dcd6-108">Return Value</span></span>  

 <span data-ttu-id="4dcd6-109">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="4dcd6-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4dcd6-110">Требования</span><span class="sxs-lookup"><span data-stu-id="4dcd6-110">Requirements</span></span>  

 <span data-ttu-id="4dcd6-111">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="4dcd6-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dcd6-112">См. также</span><span class="sxs-lookup"><span data-stu-id="4dcd6-112">See also</span></span>

- [<span data-ttu-id="4dcd6-113">Интерфейс ISymUnmanagedScope</span><span class="sxs-lookup"><span data-stu-id="4dcd6-113">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
- [<span data-ttu-id="4dcd6-114">Метод GetEndOffset</span><span class="sxs-lookup"><span data-stu-id="4dcd6-114">GetEndOffset Method</span></span>](isymunmanagedscope-getendoffset-method.md)
