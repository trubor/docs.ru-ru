---
description: 'Дополнительные сведения о методе: ISymUnmanagedVariable:: OutAttribute'
title: Метод ISymUnmanagedVariable::GetAttributes
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAttributes
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAttributes
helpviewer_keywords:
- GetAttributes method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAttributes method [.NET Framework debugging]
ms.assetid: 80f168af-a6a6-4c8f-b9e6-8a82dc834ed5
topic_type:
- apiref
ms.openlocfilehash: 0adaeaf512f129f92b7f15cdba375395a0a81855
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762842"
---
# <a name="isymunmanagedvariablegetattributes-method"></a><span data-ttu-id="7ceb9-103">Метод ISymUnmanagedVariable::GetAttributes</span><span class="sxs-lookup"><span data-stu-id="7ceb9-103">ISymUnmanagedVariable::GetAttributes Method</span></span>

<span data-ttu-id="7ceb9-104">Возвращает флаги атрибута для этой переменной.</span><span class="sxs-lookup"><span data-stu-id="7ceb9-104">Gets the attribute flags for this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ceb9-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7ceb9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAttributes(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7ceb9-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="7ceb9-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="7ceb9-107">заполняет Указатель на объект `ULONG32` , который получает атрибуты.</span><span class="sxs-lookup"><span data-stu-id="7ceb9-107">[out] A pointer to a `ULONG32` that receives the attributes.</span></span> <span data-ttu-id="7ceb9-108">Возвращаемое значение будет одним из значений, определенных в перечислении [CorSymVarFlag](corsymvarflag-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="7ceb9-108">The returned value will be one of the values defined in the [CorSymVarFlag](corsymvarflag-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7ceb9-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="7ceb9-109">Return Value</span></span>  

 <span data-ttu-id="7ceb9-110">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="7ceb9-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ceb9-111">Требования</span><span class="sxs-lookup"><span data-stu-id="7ceb9-111">Requirements</span></span>  

 <span data-ttu-id="7ceb9-112">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="7ceb9-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ceb9-113">См. также</span><span class="sxs-lookup"><span data-stu-id="7ceb9-113">See also</span></span>

- [<span data-ttu-id="7ceb9-114">Интерфейс ISymUnmanagedVariable</span><span class="sxs-lookup"><span data-stu-id="7ceb9-114">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
