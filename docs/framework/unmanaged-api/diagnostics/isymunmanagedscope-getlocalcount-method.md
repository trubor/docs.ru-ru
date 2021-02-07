---
description: 'Дополнительные сведения о методе: Исимунманажедскопе:: GetLocalCount'
title: Метод ISymUnmanagedScope::GetLocalCount
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetLocalCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetLocalCount
helpviewer_keywords:
- GetLocalCount method [.NET Framework debugging]
- ISymUnmanagedScope::GetLocalCount method [.NET Framework debugging]
ms.assetid: 3ede8fb5-f655-4088-8e19-9c53812588a8
topic_type:
- apiref
ms.openlocfilehash: 987d161d273b12810988ef30acb703973098d29c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763446"
---
# <a name="isymunmanagedscopegetlocalcount-method"></a><span data-ttu-id="39159-103">Метод ISymUnmanagedScope::GetLocalCount</span><span class="sxs-lookup"><span data-stu-id="39159-103">ISymUnmanagedScope::GetLocalCount Method</span></span>

<span data-ttu-id="39159-104">Возвращает число локальных переменных, определенных в этой области.</span><span class="sxs-lookup"><span data-stu-id="39159-104">Gets a count of the local variables defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39159-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="39159-105">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalCount(  
    [out, retval] ULONG32 *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="39159-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="39159-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="39159-107">заполняет Указатель на объект `ULONG32` , который получает число локальных переменных.</span><span class="sxs-lookup"><span data-stu-id="39159-107">[out] A pointer to a `ULONG32` that receives the count of local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="39159-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="39159-108">Return Value</span></span>  

 <span data-ttu-id="39159-109">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="39159-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39159-110">Требования</span><span class="sxs-lookup"><span data-stu-id="39159-110">Requirements</span></span>  

 <span data-ttu-id="39159-111">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="39159-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39159-112">См. также</span><span class="sxs-lookup"><span data-stu-id="39159-112">See also</span></span>

- [<span data-ttu-id="39159-113">Интерфейс ISymUnmanagedScope</span><span class="sxs-lookup"><span data-stu-id="39159-113">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
