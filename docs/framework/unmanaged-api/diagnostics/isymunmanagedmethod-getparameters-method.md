---
description: 'Дополнительные сведения о методе: ISymUnmanagedMethod:: Parameters'
title: Метод ISymUnmanagedMethod::GetParameters
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetParameters
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetParameters
helpviewer_keywords:
- ISymUnmanagedMethod::GetParameters method [.NET Framework debugging]
- GetParameters method [.NET Framework debugging]
ms.assetid: 3a8074f1-facc-4a3f-bb9b-d6574fc2fc74
topic_type:
- apiref
ms.openlocfilehash: c8860a4d42019aaacef01879b175fd45ea837f2b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721376"
---
# <a name="isymunmanagedmethodgetparameters-method"></a><span data-ttu-id="5ccd0-103">Метод ISymUnmanagedMethod::GetParameters</span><span class="sxs-lookup"><span data-stu-id="5ccd0-103">ISymUnmanagedMethod::GetParameters Method</span></span>

<span data-ttu-id="5ccd0-104">Возвращает параметры для этого метода.</span><span class="sxs-lookup"><span data-stu-id="5ccd0-104">Gets the parameters for this method.</span></span> <span data-ttu-id="5ccd0-105">Параметры возвращаются в том порядке, в котором они определены в сигнатуре метода.</span><span class="sxs-lookup"><span data-stu-id="5ccd0-105">The parameters are returned in the order in which they are defined within the method's signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ccd0-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5ccd0-106">Syntax</span></span>  
  
```cpp  
HRESULT GetParameters(  
    [in]  ULONG32  cParams,  
    [out] ULONG32  *pcParams,  
    [out, size_is(cParams),  
        length_is(*pcParams)] ISymUnmanagedVariable*  params[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ccd0-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="5ccd0-107">Parameters</span></span>  

 `cParams`  
 <span data-ttu-id="5ccd0-108">[in] Размер массива `params`.</span><span class="sxs-lookup"><span data-stu-id="5ccd0-108">[in] The size of the `params` array.</span></span>  
  
 `pcParams`  
 <span data-ttu-id="5ccd0-109">окне Указатель на объект `ULONG32` , который получает размер буфера, который требуется для хранения параметров.</span><span class="sxs-lookup"><span data-stu-id="5ccd0-109">[in] A pointer to a `ULONG32` that receives the size of the buffer that is required to contain the parameters.</span></span>  
  
 `params`  
 <span data-ttu-id="5ccd0-110">заполняет Указатель на буфер, который получает параметры.</span><span class="sxs-lookup"><span data-stu-id="5ccd0-110">[out] A pointer to the buffer that receives the parameters.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5ccd0-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="5ccd0-111">Return Value</span></span>  

 <span data-ttu-id="5ccd0-112">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="5ccd0-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ccd0-113">Требования</span><span class="sxs-lookup"><span data-stu-id="5ccd0-113">Requirements</span></span>  

 <span data-ttu-id="5ccd0-114">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="5ccd0-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ccd0-115">См. также</span><span class="sxs-lookup"><span data-stu-id="5ccd0-115">See also</span></span>

- [<span data-ttu-id="5ccd0-116">Интерфейс ISymUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="5ccd0-116">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
