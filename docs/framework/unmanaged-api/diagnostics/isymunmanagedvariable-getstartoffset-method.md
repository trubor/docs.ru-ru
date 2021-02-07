---
description: 'Дополнительные сведения о методе: ISymUnmanagedVariable:: Жетстартоффсет'
title: Метод ISymUnmanagedVariable::GetStartOffset
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetStartOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetStartOffset
helpviewer_keywords:
- GetStartOffset method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetStartOffset method [.NET Framework debugging]
ms.assetid: 63021fc1-9c2d-4788-811f-fe8ca077206a
topic_type:
- apiref
ms.openlocfilehash: 96ff27cfaf53c7a63c819b1a423e62478cf74832
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762725"
---
# <a name="isymunmanagedvariablegetstartoffset-method"></a><span data-ttu-id="efb8c-103">Метод ISymUnmanagedVariable::GetStartOffset</span><span class="sxs-lookup"><span data-stu-id="efb8c-103">ISymUnmanagedVariable::GetStartOffset Method</span></span>

<span data-ttu-id="efb8c-104">Возвращает начальное смещение этой переменной в родительском элементе.</span><span class="sxs-lookup"><span data-stu-id="efb8c-104">Gets the start offset of this variable within its parent.</span></span> <span data-ttu-id="efb8c-105">Если это локальная переменная в области, начальное смещение будет находиться в пределах смещений, определенных для области.</span><span class="sxs-lookup"><span data-stu-id="efb8c-105">If this is a local variable within a scope, the start offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efb8c-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="efb8c-106">Syntax</span></span>  
  
```cpp  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="efb8c-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="efb8c-107">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="efb8c-108">заполняет Указатель на объект `ULONG32` , который получает начальное смещение.</span><span class="sxs-lookup"><span data-stu-id="efb8c-108">[out] A pointer to a `ULONG32` that receives the start offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="efb8c-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="efb8c-109">Return Value</span></span>  

 <span data-ttu-id="efb8c-110">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="efb8c-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="efb8c-111">Требования</span><span class="sxs-lookup"><span data-stu-id="efb8c-111">Requirements</span></span>  

 <span data-ttu-id="efb8c-112">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="efb8c-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efb8c-113">См. также</span><span class="sxs-lookup"><span data-stu-id="efb8c-113">See also</span></span>

- [<span data-ttu-id="efb8c-114">Интерфейс ISymUnmanagedVariable</span><span class="sxs-lookup"><span data-stu-id="efb8c-114">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
- [<span data-ttu-id="efb8c-115">Метод GetEndOffset</span><span class="sxs-lookup"><span data-stu-id="efb8c-115">GetEndOffset Method</span></span>](isymunmanagedvariable-getendoffset-method.md)
