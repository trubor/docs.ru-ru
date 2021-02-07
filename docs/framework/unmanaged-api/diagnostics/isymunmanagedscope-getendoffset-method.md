---
description: 'Дополнительные сведения о методе: Исимунманажедскопе:: Жетендоффсет'
title: Метод ISymUnmanagedScope::GetEndOffset
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetEndOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetEndOffset
helpviewer_keywords:
- ISymUnmanagedScope::GetEndOffset method [.NET Framework debugging]
- GetEndOffset method, ISymUnmanagedScope interface [.NET Framework debugging]
ms.assetid: 1d0b15c9-8059-435f-9fce-346a08b9bd36
topic_type:
- apiref
ms.openlocfilehash: ac95b98bb87fbf3dc3b42b5a2e5413f76dfffa34
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763481"
---
# <a name="isymunmanagedscopegetendoffset-method"></a><span data-ttu-id="8addf-103">Метод ISymUnmanagedScope::GetEndOffset</span><span class="sxs-lookup"><span data-stu-id="8addf-103">ISymUnmanagedScope::GetEndOffset Method</span></span>

<span data-ttu-id="8addf-104">Возвращает конечное смещение для данной области.</span><span class="sxs-lookup"><span data-stu-id="8addf-104">Gets the end offset for this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8addf-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8addf-105">Syntax</span></span>  
  
```cpp  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8addf-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="8addf-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="8addf-107">заполняет Указатель на объект `ULONG32` , который получает конечное смещение.</span><span class="sxs-lookup"><span data-stu-id="8addf-107">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8addf-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="8addf-108">Return Value</span></span>  

 <span data-ttu-id="8addf-109">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="8addf-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8addf-110">Требования</span><span class="sxs-lookup"><span data-stu-id="8addf-110">Requirements</span></span>  

 <span data-ttu-id="8addf-111">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="8addf-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8addf-112">См. также</span><span class="sxs-lookup"><span data-stu-id="8addf-112">See also</span></span>

- [<span data-ttu-id="8addf-113">Интерфейс ISymUnmanagedScope</span><span class="sxs-lookup"><span data-stu-id="8addf-113">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
- [<span data-ttu-id="8addf-114">Метод GetStartOffset</span><span class="sxs-lookup"><span data-stu-id="8addf-114">GetStartOffset Method</span></span>](isymunmanagedscope-getstartoffset-method.md)
