---
description: 'Дополнительные сведения о методе: ISymUnmanagedVariable:: Жетендоффсет'
title: Метод ISymUnmanagedVariable::GetEndOffset
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetEndOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetEndOffset
helpviewer_keywords:
- ISymUnmanagedVariable::GetEndOffset method [.NET Framework debugging]
- GetEndOffset method, ISymUnmanagedVariable interface [.NET Framework debugging]
ms.assetid: e5d777c5-d450-4c0f-999c-b3953ee22cfb
topic_type:
- apiref
ms.openlocfilehash: 302f19c0d9fce1864e94a79efe3a3d1515478c0b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762803"
---
# <a name="isymunmanagedvariablegetendoffset-method"></a><span data-ttu-id="bd3e5-103">Метод ISymUnmanagedVariable::GetEndOffset</span><span class="sxs-lookup"><span data-stu-id="bd3e5-103">ISymUnmanagedVariable::GetEndOffset Method</span></span>

<span data-ttu-id="bd3e5-104">Возвращает конечное смещение данной переменной в родительском объекте.</span><span class="sxs-lookup"><span data-stu-id="bd3e5-104">Gets the end offset of this variable within its parent.</span></span> <span data-ttu-id="bd3e5-105">Если это локальная переменная в области, то конечное смещение будет находиться в пределах смещений, определенных для области.</span><span class="sxs-lookup"><span data-stu-id="bd3e5-105">If this is a local variable within a scope, the end offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd3e5-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="bd3e5-106">Syntax</span></span>  
  
```cpp  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bd3e5-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="bd3e5-107">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="bd3e5-108">заполняет Указатель на объект `ULONG32` , который получает конечное смещение.</span><span class="sxs-lookup"><span data-stu-id="bd3e5-108">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bd3e5-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="bd3e5-109">Return Value</span></span>  

 <span data-ttu-id="bd3e5-110">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="bd3e5-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd3e5-111">Требования</span><span class="sxs-lookup"><span data-stu-id="bd3e5-111">Requirements</span></span>  

 <span data-ttu-id="bd3e5-112">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="bd3e5-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd3e5-113">См. также</span><span class="sxs-lookup"><span data-stu-id="bd3e5-113">See also</span></span>

- [<span data-ttu-id="bd3e5-114">Интерфейс ISymUnmanagedVariable</span><span class="sxs-lookup"><span data-stu-id="bd3e5-114">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
- [<span data-ttu-id="bd3e5-115">Метод GetStartOffset</span><span class="sxs-lookup"><span data-stu-id="bd3e5-115">GetStartOffset Method</span></span>](isymunmanagedvariable-getstartoffset-method.md)
