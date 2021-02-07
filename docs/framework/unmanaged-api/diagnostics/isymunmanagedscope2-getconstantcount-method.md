---
description: 'Дополнительные сведения о методе: ISymUnmanagedScope2:: Жетконстанткаунт'
title: Метод ISymUnmanagedScope2::GetConstantCount
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope2.GetConstantCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope2::GetConstantCount
helpviewer_keywords:
- ISymUnmanagedScope2::GetConstantCount method [.NET Framework debugging]
- GetConstantCount method [.NET Framework debugging]
ms.assetid: 1e1f0be6-c4e8-4d6c-98cd-d5fa9f686e87
topic_type:
- apiref
ms.openlocfilehash: e5b084edb116432aa43360db72ca2528dd3cc6a3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763258"
---
# <a name="isymunmanagedscope2getconstantcount-method"></a><span data-ttu-id="188fe-103">Метод ISymUnmanagedScope2::GetConstantCount</span><span class="sxs-lookup"><span data-stu-id="188fe-103">ISymUnmanagedScope2::GetConstantCount Method</span></span>

<span data-ttu-id="188fe-104">Возвращает число констант, определенных в этой области.</span><span class="sxs-lookup"><span data-stu-id="188fe-104">Gets a count of the constants defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="188fe-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="188fe-105">Syntax</span></span>  
  
```cpp  
HRESULT GetConstantCount(  
    [out, retval] ULONG32 *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="188fe-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="188fe-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="188fe-107">заполняет Указатель на объект `ULONG32` , который получает размер буфера (в символах), необходимого для хранения констант.</span><span class="sxs-lookup"><span data-stu-id="188fe-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="188fe-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="188fe-108">Return Value</span></span>  

 <span data-ttu-id="188fe-109">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="188fe-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="188fe-110">Требования</span><span class="sxs-lookup"><span data-stu-id="188fe-110">Requirements</span></span>  

 <span data-ttu-id="188fe-111">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="188fe-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="188fe-112">См. также</span><span class="sxs-lookup"><span data-stu-id="188fe-112">See also</span></span>

- [<span data-ttu-id="188fe-113">Интерфейс ISymUnmanagedScope2</span><span class="sxs-lookup"><span data-stu-id="188fe-113">ISymUnmanagedScope2 Interface</span></span>](isymunmanagedscope2-interface.md)
