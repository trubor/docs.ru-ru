---
description: 'Дополнительные сведения о методе: ISymUnmanagedMethod:: Жетрутскопе'
title: Метод ISymUnmanagedMethod::GetRootScope
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetRootScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetRootScope
helpviewer_keywords:
- ISymUnmanagedMethod::GetRootScope method [.NET Framework debugging]
- GetRootScope method [.NET Framework debugging]
ms.assetid: 7d58caac-2e75-4dfa-9249-32d8a624b247
topic_type:
- apiref
ms.openlocfilehash: b1e490d8e0c5e0d60143202dd0291237685c950f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710012"
---
# <a name="isymunmanagedmethodgetrootscope-method"></a><span data-ttu-id="3d4db-103">Метод ISymUnmanagedMethod::GetRootScope</span><span class="sxs-lookup"><span data-stu-id="3d4db-103">ISymUnmanagedMethod::GetRootScope Method</span></span>

<span data-ttu-id="3d4db-104">Возвращает корневую лексическую область внутри этого метода.</span><span class="sxs-lookup"><span data-stu-id="3d4db-104">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="3d4db-105">Эта область включает весь метод.</span><span class="sxs-lookup"><span data-stu-id="3d4db-105">This scope encloses the entire method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d4db-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3d4db-106">Syntax</span></span>  
  
```cpp  
HRESULT GetRootScope(  
    [out, retval] ISymUnmanagedScope** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3d4db-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="3d4db-107">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="3d4db-108">заполняет Указатель, которому присваивается возвращаемый интерфейс [исимунманажедскопе](isymunmanagedscope-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="3d4db-108">[out] A pointer that is set to the returned [ISymUnmanagedScope](isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3d4db-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="3d4db-109">Return Value</span></span>  

 <span data-ttu-id="3d4db-110">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="3d4db-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d4db-111">Требования</span><span class="sxs-lookup"><span data-stu-id="3d4db-111">Requirements</span></span>  

 <span data-ttu-id="3d4db-112">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="3d4db-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d4db-113">См. также</span><span class="sxs-lookup"><span data-stu-id="3d4db-113">See also</span></span>

- [<span data-ttu-id="3d4db-114">Интерфейс ISymUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="3d4db-114">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
