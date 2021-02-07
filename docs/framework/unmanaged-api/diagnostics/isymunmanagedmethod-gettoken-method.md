---
description: 'См. Дополнительные сведения о методе ISymUnmanagedMethod:: методом with Token'
title: Метод ISymUnmanagedMethod::GetToken
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetToken
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetToken
helpviewer_keywords:
- ISymUnmanagedMethod::GetToken method [.NET Framework debugging]
- GetToken method, ISymUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: 4effbe95-c36e-4a45-8b2a-ee21339415fb
topic_type:
- apiref
ms.openlocfilehash: fde9936a6e79b9d1fff5b38ee7242cf5bb71369d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721311"
---
# <a name="isymunmanagedmethodgettoken-method"></a><span data-ttu-id="93fac-103">Метод ISymUnmanagedMethod::GetToken</span><span class="sxs-lookup"><span data-stu-id="93fac-103">ISymUnmanagedMethod::GetToken Method</span></span>

<span data-ttu-id="93fac-104">Возвращает маркер метаданных для данного метода.</span><span class="sxs-lookup"><span data-stu-id="93fac-104">Returns the metadata token for this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93fac-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="93fac-105">Syntax</span></span>  
  
```cpp  
HRESULT GetToken(  
   [out, retval]  mdMethodDef  *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="93fac-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="93fac-106">Parameters</span></span>  

 `pToken`  
 <span data-ttu-id="93fac-107">заполняет Указатель на объект `mdMethodDef` , который получает размер буфера (в символах), необходимого для хранения метаданных.</span><span class="sxs-lookup"><span data-stu-id="93fac-107">[out] A pointer to a `mdMethodDef` that receives the size, in characters, of the buffer required to contain the metadata.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="93fac-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="93fac-108">Return Value</span></span>  

 <span data-ttu-id="93fac-109">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="93fac-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93fac-110">Требования</span><span class="sxs-lookup"><span data-stu-id="93fac-110">Requirements</span></span>  

 <span data-ttu-id="93fac-111">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="93fac-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93fac-112">См. также</span><span class="sxs-lookup"><span data-stu-id="93fac-112">See also</span></span>

- [<span data-ttu-id="93fac-113">Интерфейс ISymUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="93fac-113">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
