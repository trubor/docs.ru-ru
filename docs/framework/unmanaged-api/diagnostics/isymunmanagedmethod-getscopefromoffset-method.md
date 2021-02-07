---
description: 'Дополнительные сведения о методе: ISymUnmanagedMethod:: GetScopeFromOffset'
title: Метод ISymUnmanagedMethod::GetScopeFromOffset
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetScopeFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetScopeFromOffset
helpviewer_keywords:
- GetScopeFromOffset method [.NET Framework debugging]
- ISymUnmanagedMethod::GetScopeFromOffset method [.NET Framework debugging]
ms.assetid: d14cf210-81f8-46e1-8b19-6ddec0ba8b11
topic_type:
- apiref
ms.openlocfilehash: 87dd1f1732ec5d7c8669dbc2bf73b0b6128aafa1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721324"
---
# <a name="isymunmanagedmethodgetscopefromoffset-method"></a><span data-ttu-id="17299-103">Метод ISymUnmanagedMethod::GetScopeFromOffset</span><span class="sxs-lookup"><span data-stu-id="17299-103">ISymUnmanagedMethod::GetScopeFromOffset Method</span></span>

<span data-ttu-id="17299-104">Возвращает наиболее окружающую лексическую область внутри этого метода, которая заключает заданное смещение.</span><span class="sxs-lookup"><span data-stu-id="17299-104">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span> <span data-ttu-id="17299-105">Это можно использовать для запуска поиска локальных переменных.</span><span class="sxs-lookup"><span data-stu-id="17299-105">This can be used to start local variable searches.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17299-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="17299-106">Syntax</span></span>  
  
```cpp  
HRESULT GetScopeFromOffset(  
    [in]  ULONG32 offset,  
    [out, retval] ISymUnmanagedScope**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17299-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="17299-107">Parameters</span></span>  

 `offset`  
 <span data-ttu-id="17299-108">окне Значение типа `ULONG` , содержащее смещение.</span><span class="sxs-lookup"><span data-stu-id="17299-108">[in] A `ULONG` that contains the offset.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="17299-109">заполняет Указатель, которому присваивается возвращаемый интерфейс [исимунманажедскопе](isymunmanagedscope-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="17299-109">[out] A pointer that is set to the returned [ISymUnmanagedScope](isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="17299-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="17299-110">Return Value</span></span>  

 <span data-ttu-id="17299-111">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="17299-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17299-112">Требования</span><span class="sxs-lookup"><span data-stu-id="17299-112">Requirements</span></span>  

 <span data-ttu-id="17299-113">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="17299-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17299-114">См. также</span><span class="sxs-lookup"><span data-stu-id="17299-114">See also</span></span>

- [<span data-ttu-id="17299-115">Интерфейс ISymUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="17299-115">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
