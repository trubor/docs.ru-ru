---
description: 'Дополнительные сведения о методе: ISymUnmanagedNamespace:: namespace'
title: Метод ISymUnmanagedNamespace::GetNamespaces
ms.date: 03/30/2017
api_name:
- ISymUnmanagedNamespace.GetNamespaces
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedNamespace::GetNamespaces
helpviewer_keywords:
- ISymUnmanagedNamespace::GetNamespaces method [.NET Framework debugging]
- GetNamespaces method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: 0ea9d9af-8709-4a46-872b-f54d9e840088
topic_type:
- apiref
ms.openlocfilehash: f17b16e2a3a7001d16c86dd6dc95241c1b0785e6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709910"
---
# <a name="isymunmanagednamespacegetnamespaces-method"></a><span data-ttu-id="c3f00-103">Метод ISymUnmanagedNamespace::GetNamespaces</span><span class="sxs-lookup"><span data-stu-id="c3f00-103">ISymUnmanagedNamespace::GetNamespaces Method</span></span>

<span data-ttu-id="c3f00-104">Возвращает дочерние элементы этого пространства имен.</span><span class="sxs-lookup"><span data-stu-id="c3f00-104">Gets the children of this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3f00-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c3f00-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespaces(  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is(cNameSpaces), length_is(*pcNameSpaces)]  
        ISymUnmanagedNamespace* namespaces[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3f00-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="c3f00-106">Parameters</span></span>  

 `cNameSpaces`  
 <span data-ttu-id="c3f00-107">окне Значение типа `ULONG32` , указывающее размер `namespaces` массива.</span><span class="sxs-lookup"><span data-stu-id="c3f00-107">[in] A `ULONG32` that indicates the size of the `namespaces` array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="c3f00-108">заполняет Указатель на объект `ULONG32` , который получает размер буфера (в символах), необходимого для хранения пространств имен.</span><span class="sxs-lookup"><span data-stu-id="c3f00-108">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the namespaces.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="c3f00-109">заполняет Указатель на буфер, содержащий пространства имен.</span><span class="sxs-lookup"><span data-stu-id="c3f00-109">[out] A pointer to the buffer that contains the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c3f00-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="c3f00-110">Return Value</span></span>  

 <span data-ttu-id="c3f00-111">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="c3f00-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3f00-112">Требования</span><span class="sxs-lookup"><span data-stu-id="c3f00-112">Requirements</span></span>  

 <span data-ttu-id="c3f00-113">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="c3f00-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3f00-114">См. также</span><span class="sxs-lookup"><span data-stu-id="c3f00-114">See also</span></span>

- [<span data-ttu-id="c3f00-115">Интерфейс ISymUnmanagedNamespace</span><span class="sxs-lookup"><span data-stu-id="c3f00-115">ISymUnmanagedNamespace Interface</span></span>](isymunmanagednamespace-interface.md)
