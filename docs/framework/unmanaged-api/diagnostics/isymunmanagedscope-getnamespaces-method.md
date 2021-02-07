---
description: 'Дополнительные сведения о методе: Исимунманажедскопе:: namespace'
title: Метод ISymUnmanagedScope::GetNamespaces
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetNamespaces
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetNamespaces
helpviewer_keywords:
- GetNamespaces method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetNamespaces method [.NET Framework debugging]
ms.assetid: c44b0440-04bd-460a-84fb-41afecf44503
topic_type:
- apiref
ms.openlocfilehash: 39b6507845e911cafc9b9ab38f7b67cdf1fdf2c5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763349"
---
# <a name="isymunmanagedscopegetnamespaces-method"></a><span data-ttu-id="428bd-103">Метод ISymUnmanagedScope::GetNamespaces</span><span class="sxs-lookup"><span data-stu-id="428bd-103">ISymUnmanagedScope::GetNamespaces Method</span></span>

<span data-ttu-id="428bd-104">Возвращает пространства имен, используемые в этой области.</span><span class="sxs-lookup"><span data-stu-id="428bd-104">Gets the namespaces that are being used within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="428bd-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="428bd-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespaces(  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is(cNameSpaces),  
        length_is(*pcNameSpaces)]  
        ISymUnmanagedNamespace* namespaces[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="428bd-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="428bd-106">Parameters</span></span>  

 `cNameSpaces`  
 <span data-ttu-id="428bd-107">[in] Размер массива `namespaces`.</span><span class="sxs-lookup"><span data-stu-id="428bd-107">[in] The size of the `namespaces` array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="428bd-108">заполняет Указатель на объект `ULONG32` , который получает размер буфера, необходимого для хранения пространств имен.</span><span class="sxs-lookup"><span data-stu-id="428bd-108">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the namespaces.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="428bd-109">заполняет Массив, получающий пространства имен.</span><span class="sxs-lookup"><span data-stu-id="428bd-109">[out] The array that receives the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="428bd-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="428bd-110">Return Value</span></span>  

 <span data-ttu-id="428bd-111">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="428bd-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="428bd-112">Требования</span><span class="sxs-lookup"><span data-stu-id="428bd-112">Requirements</span></span>  

 <span data-ttu-id="428bd-113">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="428bd-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="428bd-114">См. также</span><span class="sxs-lookup"><span data-stu-id="428bd-114">See also</span></span>

- [<span data-ttu-id="428bd-115">Интерфейс ISymUnmanagedScope</span><span class="sxs-lookup"><span data-stu-id="428bd-115">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
