---
description: 'Дополнительные сведения о методе: Исимунманажедскопе:: Parent'
title: Метод ISymUnmanagedScope::GetParent
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetParent
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetParent
helpviewer_keywords:
- GetParent method [.NET Framework debugging]
- ISymUnmanagedScope::GetParent method [.NET Framework debugging]
ms.assetid: c7963c87-6ec5-49b3-a5cd-e0fe0c43f9b4
topic_type:
- apiref
ms.openlocfilehash: c6a056c828bfaefd171ef3f0c546d93d30fb6863
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763336"
---
# <a name="isymunmanagedscopegetparent-method"></a><span data-ttu-id="0dca1-103">Метод ISymUnmanagedScope::GetParent</span><span class="sxs-lookup"><span data-stu-id="0dca1-103">ISymUnmanagedScope::GetParent Method</span></span>

<span data-ttu-id="0dca1-104">Возвращает родительскую область этой области.</span><span class="sxs-lookup"><span data-stu-id="0dca1-104">Gets the parent scope of this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0dca1-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0dca1-105">Syntax</span></span>  
  
```cpp  
HRESULT GetParent(  
    [out, retval] ISymUnmanagedScope** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0dca1-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="0dca1-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="0dca1-107">заполняет Указатель на возвращаемый интерфейс [исимунманажедскопе](isymunmanagedscope-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="0dca1-107">[out] A pointer to the returned [ISymUnmanagedScope](isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0dca1-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="0dca1-108">Return Value</span></span>  

 <span data-ttu-id="0dca1-109">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="0dca1-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0dca1-110">Требования</span><span class="sxs-lookup"><span data-stu-id="0dca1-110">Requirements</span></span>  

 <span data-ttu-id="0dca1-111">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="0dca1-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0dca1-112">См. также</span><span class="sxs-lookup"><span data-stu-id="0dca1-112">See also</span></span>

- [<span data-ttu-id="0dca1-113">Интерфейс ISymUnmanagedScope</span><span class="sxs-lookup"><span data-stu-id="0dca1-113">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
- [<span data-ttu-id="0dca1-114">Метод GetChildren</span><span class="sxs-lookup"><span data-stu-id="0dca1-114">GetChildren Method</span></span>](isymunmanagedscope-getchildren-method.md)
