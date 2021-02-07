---
description: 'Дополнительные сведения о методе: Исимунманажедскопе:: Children'
title: Метод ISymUnmanagedScope::GetChildren
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetChildren
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetChildren
helpviewer_keywords:
- ISymUnmanagedScope::GetChildren method [.NET Framework debugging]
- GetChildren method [.NET Framework debugging]
ms.assetid: 0bed524e-cc48-4bf0-b9fa-25d665e63ddb
topic_type:
- apiref
ms.openlocfilehash: 55d72c98d34fcb30a479611895228fbc1b9f7f55
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763505"
---
# <a name="isymunmanagedscopegetchildren-method"></a><span data-ttu-id="bf5e1-103">Метод ISymUnmanagedScope::GetChildren</span><span class="sxs-lookup"><span data-stu-id="bf5e1-103">ISymUnmanagedScope::GetChildren Method</span></span>

<span data-ttu-id="bf5e1-104">Возвращает дочерние элементы этой области.</span><span class="sxs-lookup"><span data-stu-id="bf5e1-104">Gets the children of this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf5e1-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="bf5e1-105">Syntax</span></span>  
  
```cpp  
HRESULT GetChildren(  
    [in]  ULONG32  cChildren,  
    [out] ULONG32  *pcChildren,  
    [out, size_is(cChildren),  
        length_is(*pcChildren)] ISymUnmanagedScope* children[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf5e1-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="bf5e1-106">Parameters</span></span>  

 `cChildren`  
 <span data-ttu-id="bf5e1-107">окне Значение типа `ULONG32` , указывающее размер `children` массива.</span><span class="sxs-lookup"><span data-stu-id="bf5e1-107">[in] A `ULONG32` that indicates the size of the `children` array.</span></span>  
  
 `pcChildren`  
 <span data-ttu-id="bf5e1-108">заполняет Указатель на объект `ULONG32` , который получает размер буфера, необходимого для хранения дочерних элементов.</span><span class="sxs-lookup"><span data-stu-id="bf5e1-108">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the children.</span></span>  
  
 `children`  
 <span data-ttu-id="bf5e1-109">заполняет Возвращаемый массив дочерних элементов.</span><span class="sxs-lookup"><span data-stu-id="bf5e1-109">[out] The returned array of children.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bf5e1-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="bf5e1-110">Return Value</span></span>  

 <span data-ttu-id="bf5e1-111">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="bf5e1-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf5e1-112">Требования</span><span class="sxs-lookup"><span data-stu-id="bf5e1-112">Requirements</span></span>  

 <span data-ttu-id="bf5e1-113">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="bf5e1-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf5e1-114">См. также</span><span class="sxs-lookup"><span data-stu-id="bf5e1-114">See also</span></span>

- [<span data-ttu-id="bf5e1-115">Интерфейс ISymUnmanagedScope</span><span class="sxs-lookup"><span data-stu-id="bf5e1-115">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
- [<span data-ttu-id="bf5e1-116">Метод GetParent</span><span class="sxs-lookup"><span data-stu-id="bf5e1-116">GetParent Method</span></span>](isymunmanagedscope-getparent-method.md)
