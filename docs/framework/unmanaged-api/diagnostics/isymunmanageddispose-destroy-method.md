---
description: 'Дополнительные сведения о методе: ISymUnmanagedDispose::D естрой'
title: Метод ISymUnmanagedDispose::Destroy
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDispose.Destroy
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDispose::Destroy
helpviewer_keywords:
- ISymUnmanagedDispose::Destroy method [.NET Framework debugging]
- Destroy method [.NET Framework debugging]
ms.assetid: a854ab9f-d2ba-470e-867f-808c1e7bd07a
topic_type:
- apiref
ms.openlocfilehash: 3c13f90e08f2ba0dd7c70acc3321913b14195f1c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790208"
---
# <a name="isymunmanageddisposedestroy-method"></a><span data-ttu-id="2eef7-103">Метод ISymUnmanagedDispose::Destroy</span><span class="sxs-lookup"><span data-stu-id="2eef7-103">ISymUnmanagedDispose::Destroy Method</span></span>

<span data-ttu-id="2eef7-104">Заставляет базовый объект освобождать все внутренние ссылки и возвращать ошибку при любом последующем вызове метода.</span><span class="sxs-lookup"><span data-stu-id="2eef7-104">Causes the underlying object to release all internal references and return failure on any subsequent method calls.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2eef7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2eef7-105">Syntax</span></span>  
  
```cpp  
HRESULT Destroy();  
```  
  
## <a name="return-value"></a><span data-ttu-id="2eef7-106">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="2eef7-106">Return Value</span></span>  

 <span data-ttu-id="2eef7-107">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="2eef7-107">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2eef7-108">Требования</span><span class="sxs-lookup"><span data-stu-id="2eef7-108">Requirements</span></span>  

 <span data-ttu-id="2eef7-109">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="2eef7-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2eef7-110">См. также</span><span class="sxs-lookup"><span data-stu-id="2eef7-110">See also</span></span>

- [<span data-ttu-id="2eef7-111">Интерфейс ISymUnmanagedDispose</span><span class="sxs-lookup"><span data-stu-id="2eef7-111">ISymUnmanagedDispose Interface</span></span>](isymunmanageddispose-interface.md)
