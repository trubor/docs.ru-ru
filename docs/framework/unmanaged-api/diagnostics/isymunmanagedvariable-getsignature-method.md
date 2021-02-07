---
description: 'Дополнительные сведения о методе: ISymUnmanagedVariable:: Signature'
title: Метод ISymUnmanagedVariable::GetSignature
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetSignature
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetSignature
helpviewer_keywords:
- GetSignature method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetSignature method [.NET Framework debugging]
ms.assetid: 78c1ba28-a410-4360-805c-23a95408964a
topic_type:
- apiref
ms.openlocfilehash: 6e8242581cf2d59563b6193ed7c7686292cbf775
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762738"
---
# <a name="isymunmanagedvariablegetsignature-method"></a><span data-ttu-id="dd635-103">Метод ISymUnmanagedVariable::GetSignature</span><span class="sxs-lookup"><span data-stu-id="dd635-103">ISymUnmanagedVariable::GetSignature Method</span></span>

<span data-ttu-id="dd635-104">Возвращает сигнатуру этой переменной.</span><span class="sxs-lookup"><span data-stu-id="dd635-104">Gets the signature of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd635-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="dd635-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dd635-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="dd635-106">Parameters</span></span>  

 `cSig`  
 <span data-ttu-id="dd635-107">окне Длина буфера, на который указывает `sig` параметр.</span><span class="sxs-lookup"><span data-stu-id="dd635-107">[in] The length of the buffer pointed to by the `sig` parameter.</span></span>  
  
 `pcSig`  
 <span data-ttu-id="dd635-108">заполняет Указатель на объект `ULONG32` , который получает размер (в символах) буфера, необходимого для хранения подписи.</span><span class="sxs-lookup"><span data-stu-id="dd635-108">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the signature.</span></span>  
  
 `sig`  
 <span data-ttu-id="dd635-109">заполняет Буфер, в котором хранится подпись.</span><span class="sxs-lookup"><span data-stu-id="dd635-109">[out] The buffer that stores the signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dd635-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="dd635-110">Return Value</span></span>  

 <span data-ttu-id="dd635-111">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="dd635-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd635-112">Требования</span><span class="sxs-lookup"><span data-stu-id="dd635-112">Requirements</span></span>  

 <span data-ttu-id="dd635-113">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="dd635-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd635-114">См. также</span><span class="sxs-lookup"><span data-stu-id="dd635-114">See also</span></span>

- [<span data-ttu-id="dd635-115">Интерфейс ISymUnmanagedVariable</span><span class="sxs-lookup"><span data-stu-id="dd635-115">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
