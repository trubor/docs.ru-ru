---
description: 'Дополнительные сведения о методе Исимунманажедскопе:: Localization.'
title: Метод ISymUnmanagedScope::GetLocals
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetLocals
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetLocals
helpviewer_keywords:
- GetLocals method [.NET Framework debugging]
- ISymUnmanagedScope::GetLocals method [.NET Framework debugging]
ms.assetid: 17c45f15-8c44-44da-b070-f902077b36e4
topic_type:
- apiref
ms.openlocfilehash: 6b20d8a79e826be0bd191d46e794f8dad45c4810
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763414"
---
# <a name="isymunmanagedscopegetlocals-method"></a><span data-ttu-id="2fe9f-103">Метод ISymUnmanagedScope::GetLocals</span><span class="sxs-lookup"><span data-stu-id="2fe9f-103">ISymUnmanagedScope::GetLocals Method</span></span>

<span data-ttu-id="2fe9f-104">Возвращает локальные переменные, определенные в этой области.</span><span class="sxs-lookup"><span data-stu-id="2fe9f-104">Gets the local variables defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fe9f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2fe9f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetLocals(  
    [in]  ULONG32  cLocals,  
    [out] ULONG32  *pcLocals,  
    [out, size_is(cLocals),  
        length_is(*pcLocals)] ISymUnmanagedVariable* locals[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2fe9f-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="2fe9f-106">Parameters</span></span>  

 `cLocals`  
 <span data-ttu-id="2fe9f-107">окне Значение типа `ULONG32` , указывающее размер `locals` массива.</span><span class="sxs-lookup"><span data-stu-id="2fe9f-107">[in] A `ULONG32` that indicates the size of the `locals` array.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="2fe9f-108">заполняет Указатель на объект `ULONG32` , который получает размер буфера, необходимого для хранения локальных переменных.</span><span class="sxs-lookup"><span data-stu-id="2fe9f-108">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the local variables.</span></span>  
  
 `locals`  
 <span data-ttu-id="2fe9f-109">заполняет Массив, который получает локальные переменные.</span><span class="sxs-lookup"><span data-stu-id="2fe9f-109">[out] The array that receives the local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2fe9f-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="2fe9f-110">Return Value</span></span>  

 <span data-ttu-id="2fe9f-111">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="2fe9f-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2fe9f-112">Требования</span><span class="sxs-lookup"><span data-stu-id="2fe9f-112">Requirements</span></span>  

 <span data-ttu-id="2fe9f-113">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="2fe9f-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fe9f-114">См. также</span><span class="sxs-lookup"><span data-stu-id="2fe9f-114">See also</span></span>

- [<span data-ttu-id="2fe9f-115">Интерфейс ISymUnmanagedScope</span><span class="sxs-lookup"><span data-stu-id="2fe9f-115">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
