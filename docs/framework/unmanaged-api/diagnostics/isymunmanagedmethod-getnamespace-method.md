---
description: 'Дополнительные сведения о методе: ISymUnmanagedMethod::/namespace'
title: Метод ISymUnmanagedMethod::GetNamespace
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetNamespace
helpviewer_keywords:
- ISymUnmanagedMethod::GetNamespace method [.NET Framework debugging]
- GetNamespace method [.NET Framework debugging]
ms.assetid: 7fbbac42-b966-406d-9ae9-67bf3aea74ce
topic_type:
- apiref
ms.openlocfilehash: 8cb211b1047aff31cc4f12d538fee414c578155b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721415"
---
# <a name="isymunmanagedmethodgetnamespace-method"></a><span data-ttu-id="e6c4f-103">Метод ISymUnmanagedMethod::GetNamespace</span><span class="sxs-lookup"><span data-stu-id="e6c4f-103">ISymUnmanagedMethod::GetNamespace Method</span></span>

<span data-ttu-id="e6c4f-104">Возвращает пространство имен, в котором определен этот метод.</span><span class="sxs-lookup"><span data-stu-id="e6c4f-104">Gets the namespace within which this method is defined.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6c4f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e6c4f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespace(  
   [out] ISymUnmanagedNamespace  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6c4f-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="e6c4f-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="e6c4f-107">заполняет Указатель, которому присваивается возвращаемый интерфейс [ISymUnmanagedNamespace](isymunmanagednamespace-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="e6c4f-107">[out] A pointer that is set to the returned [ISymUnmanagedNamespace](isymunmanagednamespace-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e6c4f-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="e6c4f-108">Return Value</span></span>  

 <span data-ttu-id="e6c4f-109">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="e6c4f-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6c4f-110">Требования</span><span class="sxs-lookup"><span data-stu-id="e6c4f-110">Requirements</span></span>  

 <span data-ttu-id="e6c4f-111">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="e6c4f-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6c4f-112">См. также</span><span class="sxs-lookup"><span data-stu-id="e6c4f-112">See also</span></span>

- [<span data-ttu-id="e6c4f-113">Интерфейс ISymUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="e6c4f-113">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
