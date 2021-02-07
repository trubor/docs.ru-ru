---
description: 'Дополнительные сведения о методе: Исимунманажедскопе:: Method'
title: Метод ISymUnmanagedScope::GetMethod
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetMethod
helpviewer_keywords:
- GetMethod method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetMethod method [.NET Framework debugging]
ms.assetid: a61866ee-221a-45b9-a1b7-395825b77872
topic_type:
- apiref
ms.openlocfilehash: 7dfc5f41d849d47bfaf600e40a7ccc9dd45da676
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763401"
---
# <a name="isymunmanagedscopegetmethod-method"></a><span data-ttu-id="7a109-103">Метод ISymUnmanagedScope::GetMethod</span><span class="sxs-lookup"><span data-stu-id="7a109-103">ISymUnmanagedScope::GetMethod Method</span></span>

<span data-ttu-id="7a109-104">Возвращает метод, содержащий эту область.</span><span class="sxs-lookup"><span data-stu-id="7a109-104">Gets the method that contains this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a109-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7a109-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethod(  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7a109-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="7a109-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="7a109-107">заполняет Указатель на возвращаемый интерфейс [ISymUnmanagedMethod](isymunmanagedmethod-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="7a109-107">[out] A pointer to the returned [ISymUnmanagedMethod](isymunmanagedmethod-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7a109-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="7a109-108">Return Value</span></span>  

 <span data-ttu-id="7a109-109">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="7a109-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a109-110">Требования</span><span class="sxs-lookup"><span data-stu-id="7a109-110">Requirements</span></span>  

 <span data-ttu-id="7a109-111">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="7a109-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a109-112">См. также</span><span class="sxs-lookup"><span data-stu-id="7a109-112">See also</span></span>

- [<span data-ttu-id="7a109-113">Интерфейс ISymUnmanagedScope</span><span class="sxs-lookup"><span data-stu-id="7a109-113">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
